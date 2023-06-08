# CSE185_FinalProject
We are making a tool to find peaks given transcription factor data. We will take an input of a tag directory of a certain input genome and a control genome for comparison, and then utilize an approach to estimate where the peaks are.   
Our output will be a .BED file written to the directory of the user's choice.  
Tag directories MUST be generated prior to running our program, with tag files in the TSV format. Tag directories can be created using HOMER's makeTagDirectory command. http://homer.ucsd.edu/homer/ngs/tagDir.html
Tag directories MUST share file names for respective chromosomes and end with .tags.tsv (i.e tag file for chromosome 17 must be 17.tags.tsv in both directories). 

# Calling the Function:
```bash
python PeakFinder.py <tag_directory_path> <control_tag_directory_path> -O <optional_output_path> 
```
Example:
```bash
python peakFinder.py tagdirs/Sox2/ tagdirs/input/ -O example.bed
```

# How to Test Our Function:
call test.py to test out our tag directory processing. It will print out a dictionary with the chromosome number, and a dictionary for the chromosome with its base pair position, with values of the read counts at each position. Although not fully implemented, testPeaks() will call the peak finding function given a window of set size, and use the window to find peaks in that window range.

# File Format:
The output file format is going to be a BED file. It will give positions from start to end of the predicted peaks, as well as their respective p-values. It will be done by our makeBED() function

# To download:
To download our repository into your system, run the command:

git clone https://github.com/hbcheng7/CSE185_FinalProject.git

# Benchmarking 
To benchmark the code to see if peaks match, run Homer's command:

makeUCSCfile <tag-directory> -o auto
The output of this will be a bedGraph file. This file will allow you to visualize the peaks in IGV, and then you can check if your peak regions match the ones of the bedGraph file.
