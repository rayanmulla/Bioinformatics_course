# Bioinformatics_course Week3 Assignment
## Data Wrangling

#### Go to ncbi.nlm.nih.gov/datasets/
#### Download genomes of bacteria specified in assignment document (14 complete genomes of bacteria up to 2001)

### Copy zip file from local path onto IBEX
	$ scp /local/path/to/zipfile user: /path/to/ibex
#### user: mullara@ilogin.ibex.kaust.edu.sa

### Create github account and repository following information on Week1 Assignment

### Clone git repository on IBEX
	$ git clone https://github.com/rayanmulla/Bioinformatics_course.git

### Download text editor emacs from the web

### Edit README.md file in emacs
	$ emacs README.md
### Commit changes to github repository(after editing)
	$ git add README.md
	$ git commit -m "Added README.md"
### Push changes
	$ git push
#### type in username and Personal Access Token generated from github account settings

### Smallest genome sizes
	$ sort -t$'\t' -k11,11n data_summary.tsv | head -n 2 | cut -f1,11 | uniq
### Output: 
	Organism Scientific Name		Size
	Chlamydia trachomatis D/UW-3/CX		1042519

### Largest genome size
	$ sort -t$'\t' -k11,11nr data_summary.tsv | head -n 2 | cut -f1,11 | uniq
### Output: 
	Organism Scientific Name        		Size
	Vibrio cholerae O1 biovar El Tor str. N16961	4033464

### Number of genomes containing at least two "c"s in species name
	cut -f1 data_summary.tsv | tail -n +2 | sort -t$'\t' -k1 | uniq | grep -c "c.*c"
### Output: 
	5 

### Number of species names containing 2 or more "c"s but not the word "coccus"
	$ cut -f1 data_summary.tsv | tail -n +2 | sort | uniq | grep "c.*c" | grep -v "coccus" | wc -l
### Output: 
	3

### Using find command to find all genome files (FASTA) larger than 3Mb
	$ find . -name "*.fna" -size +3M | wc -l
### Output: 
	6 


