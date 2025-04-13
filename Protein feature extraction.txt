# Load necessary libraries
library("protr")
library("foreign")
library("Peptides")

setwd("D:/Dataset")

# Read protein sequences from FASTA files
seq_class1 <- readFASTA("D:/Dataset/Protein.fasta")
seq_class2 <- readFASTA("D:/Dataset/Non_protein.fasta")

# Filter valid protein sequences
seq_class1 <- seq_class1[sapply(seq_class1, protcheck)]
seq_class2 <- seq_class2[sapply(seq_class2, protcheck)]

# Define the list of functions to extract features
func2perform <- c( 'extractDC', 'extractTC', 'extractCTDC', 'extractCTDD', 
                   'extractCTDT' , 'extractAPAAC', 'extractAAC')

# Loop over each function to extract features
for (f in func2perform) {
  print(f)  # Print the current function name
  
  # Dynamically call the extraction function using get()
  class1 <- t(sapply(seq_class1, function(seq) do.call(get(f), list(seq))))
  class2 <- t(sapply(seq_class2, function(seq) do.call(get(f), list(seq))))
  
  # Create directory for results
  dir.create(file.path("D:/Dataset/Result/", f), showWarnings = FALSE)
  
  # Define output file paths
  outputfile_csv_class1 <- paste("D:/Dataset/Result/", f, "/", f, "_Protein.csv", sep = "")
  outputfile_csv_class2 <- paste("D:/Dataset/Result/", f, "/", f, "_Non_protein.csv", sep = "")
  
  # Write the extracted features to CSV files
  write.table(class1, outputfile_csv_class1, sep = ",", row.names = FALSE)
  write.table(class2, outputfile_csv_class2, sep = ",", row.names = FALSE)
  
  # Read the CSV files and add labels
  data_class1 <- read.csv(outputfile_csv_class1, header = TRUE)
  data_class1$label <- "Positive"
  data_class2 <- read.csv(outputfile_csv_class2, header = TRUE)
  data_class2$label <- "Negative"
  
  
  
  # Combine the data into a single data frame
  mydata <- rbind(data_class1, data_class2)
  
  # Define ARFF output file path
  outputfile_arff <- paste("D:/Dataset/Result/", f, "/", f, ".arff", sep = "")
  
  # Write the combined data to an ARFF file
  write.arff(x = mydata, file = outputfile_arff)
}
