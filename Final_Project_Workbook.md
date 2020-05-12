# Analysis of Influenza H18N11 and H17N10 Hemagglutinin and Neuraminidase Proteins Through BLAST Analysis and Phylogenomic to Access Zoonotic Potential
This is the workbook being used for my project on human succeptibility to bat influenza.
# Background
  It has recenty been discovered that bats are hosts for two unique strands of Influenza A virus: H18N11 and H17N10. Due to these viruses being newly discovered little is known about the viruses' zoonotic potential. This study is designed to access H17N10 and H18N11's zoonotic potential through analysis of the hemagglutinin (HA) and neuraminidase (NA) proteins. HA and NA are essential proteins involved in the influenza virus' replication. If the virus lacked these proteins it wouldn't be able to replicate, and thus lose its virulence factor.  This study analyzes the potential zoonosis of the HA and NA proteins in H17N10 and H178N11 through the use of BLAST and phylogenomic analysis.

# The Setup: The Materials and Programs Needed for these Analyses
Materials Needed:
 * PC for coding (A Lenova Yoga 730 was used in this study)
 * Preffered coding terminal (PuTTY was used in this study)
 * A high preformance cluster (Ron was used in this study)
 * An Atmosphere/Jetstream account is recommended, however it was not utilized in this study due to connectivity and speed issues.
 * Access to ENA database (https://www.ebi.ac.uk/ena/browser/home)
 
Programs Utilized:
 * BLAST
 * MAFFT
 * iqTree
 * FigTree v1.4.4 (which can be downloaded from: https://github.com/rambaut/figtree/releases)
# Setting up and Downloading Programs 
The first step for our analysis was to log onto Ron and to create a new directory to house our downloaded data in:
	
	mkdir Influenza_Analysis
Then we can move into our newly made directory:
 	
	cd  Influenza_Analysis
While Jetstream wasn't used in this analysis due to connectivity issues, a "Ubuntu 18_04 Devel and Docker" instance with a M1.xxlarge size is recommended.
Now that our setup is complete we can move onto the analyses.
# BLAST
The BLAST analysis of the HA and NA proteins of H17N10 and H18N11 is done to access if the two bat-derived influenza strains share genes with human-infecting influenza strains. The human strains used for this BLAST analysis are H1N1, H2N2, H3N2, and H5N1. The BLAST anlaysis is broken down into 4 parts:BLAST Analysis of H17N10's HA protein, BLAST Analysis of H18N11's HA protein, BLAST Analysis of H17N10's NA protein, BLAST Analysis of H18N11's NA protein.
# Blast Analysis of H17N10's HA protein
The BLAST analysis of H17N10's HA protein begins with downloading and formating the imported data from the ENA database:

    #Download H1N1
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABP49327.1?download=true
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABP49327.1?download=true >H1N1_HA.fasta
    #Download H2N2
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAA64365.1?download=true
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAA64365.1?download=true >H2N2_HA.fasta
    #Download H3N2
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIZ07211.1?download=true
	          awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AIZ07211.1?download=true > H3N2_HA.fasta
    #Download H5N1
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABD28180.1?download=true
	          awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABD28180.1?download=true >H5N1_HA.fasta
    #Download H17N10
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/CY103892.1?download=true 
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CY103892.1?download=true >H17N10_HA.fasta
The human-infecting influenza strains are then combined into a fasta file to be used as a reference database in the BLAST analyis:

             cat H1N1_HA.fasta H2N2_HA.fasta H3N2_HA.fasta H5N1_HA.fasta > Human_Influenza_Viruses.fasta
	     
  A BLAST database is then made:
       
       makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
  "- in" is signiling the file input. This should be the output of your previous cat command.
  "-out" is signaling the output file. This is what you want your database is referencing
  "prot" is signaling that the data being used in this acessment is protein coded data
  
  
  A BLAST analysis can then occur using the H17N10 as our query, or our file of interest:
  
        blastp -db influenza -max_target_seqs 1 -query H17H10_HA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
   
   The BLAST file can then be viewed using:
   
          less blast.out
Due to Ron's limited space all files should be removed using the rm command.
The "ls" command can then be used to ensure our directory is clear.
# Blast Analysis of H18N11's HA protein
Similar to the above coding, the BLAST analysis of H18N11's HA protein begins with downloading and formating the imported data from the ENA database:

    #Download H1N1
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABP49327.1?download=true
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABP49327.1?download=true >H1N1_HA.fasta
    #Download H2N2
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAA64365.1?download=true
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAA64365.1?download=true >H2N2_HA.fasta
    #Download H3N2
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIZ07211.1?download=true
	          awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AIZ07211.1?download=true > H3N2_HA.fasta
    #Download H5N1
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABD28180.1?download=true
	          awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABD28180.1?download=true >H5N1_HA.fasta
    #Download H18N11
            curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/CY125945.1?download=true
            awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CY125945.1?download=true > H18N11_HA.fasta
Again, the human-infecting influenza strains are then combined into a fasta file to be used as a reference database in the BLAST analyis:

            cat H1N1_HA.fasta H2N2_HA.fasta H3N2_HA.fasta H5N1_HA.fasta > Human_Influenza_Viruses.fasta
  A BLAST database is then made:
  
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
  "- in" is signiling the file input. This should be the output of your previous cat command.
  "-out" is signaling the output file. This is what you want your database is referencing
  "prot" is signaling that the data being used in this acessment is protein coded data
  
  A BLAST analysis can then occur using the H18N11 as our query, or our file of interest:
       
       blastp -db influenza -max_target_seqs 1 -query H18H11_HA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out

 The BLAST file can then be viewed using:
   
          less blast.out
Again, due to Ron's limited space all files should be removed using the rm command.     
 The "ls" command can then be used to ensure our directory is clear.
 
# Blast Analysis of H17N10's NA protein
Similar to the above codings, the BLAST analysis of H17N10's NA protein begins with downloading and formating the imported data from the ENA database:

    #Download H1N1
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABO38057.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABO38057.1?download=true >H1N1_NA.fasta
    #Download H2N2
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACD56327.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACD56327.1?download=true >H2N2_NA.fasta
    #Download H3N2
         curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJE63100.1?download=true
	       awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJE63100.1?download=true > H3N2_NA.fasta
    #Download H5N1
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ANJ61441.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ANJ61441.1?download=true > H5N1_NA.fasta
    #Download H17N10
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFC35430.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFC35430.1?download=true >H17N10_NA.fasta
Once again, the human-infecting influenza strains are then combined into a fasta file to be used as a reference database in the BLAST analyis:

            cat H1N1_NA.fasta H2N2_NA.fasta H3N2_NA.fasta H5N1_NA.fasta > Human_Influenza_Viruses.fasta

 A BLAST database is then made:
  
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
 "- in" is signiling the file input. This should be the output of your previous cat command.
  "-out" is signaling the output file. This is what you want your database is referencing
  "prot" is signaling that the data being used in this acessment is protein coded data
  
  A BLAST analysis can then occur using the H17N10 as our query, or our file of interest:

        blastp -db influenza -max_target_seqs 1 -query H17H10_NA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
 The BLAST file can then be viewed using:
   
          less blast.out
Again, due to Ron's limited space all files should be removed using the rm command.   
 The "ls" command can then be used to ensure our directory is clear.   
    
    
# Blast Analysis of H18N11's NA protein
Similar to the above codings, the BLAST analysis of H18N11's NA protein begins with downloading and formating the imported data from the ENA database:

     #Download H1N1
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABO38057.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABO38057.1?download=true >H1N1_NA.fasta
    #Download H2N2
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACD56327.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACD56327.1?download=true >H2N2_NA.fasta
    #Download H3N2
         curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJE63100.1?download=true
	       awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJE63100.1?download=true > H3N2_NA.fasta
    #Download H5N1
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ANJ61441.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ANJ61441.1?download=true > H5N1_NA.fasta
    #Download H18N11
        curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGX84936.1?download=true
        awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGX84936.1?download=true > H18N11_NA.fasta
Once again, the human-infecting influenza strains are then combined into a fasta file to be used as a reference database in the BLAST analyis:	
	
            cat H1N1_NA.fasta H2N2_NA.fasta H3N2_NA.fasta H5N1_NA.fasta > Human_Influenza_Viruses.fasta
  A BLAST database is then made:

        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
 "- in" is signiling the file input. This should be the output of your previous cat command.
  "-out" is signaling the output file. This is what you want your database is referencing
  "prot" is signaling that the data being used in this acessment is protein coded data	
  
 A BLAST analysis can then occur using the H18N11 as our query, or our file of interest:
	
        blastp -db influenza -max_target_seqs 1 -query H18H11_NA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
   
 The BLAST file can then be viewed using:
   
          less blast.out
Again, due to Ron's limited space all files should be removed using the rm command.  
The "ls" command can then be used to ensure our directory is clear.

*Disclaimer: If using Jetstream or coding platform with a large storage component then the file from each BLAST analysis do not have to be removed right away. Our study choose to remove the data ater each analysis to avoid any coding complications. If one of these larger storage component platforms are used it is recommended that the cat file for each indvidual BLAST analysis has ts own unique name to avoid complication.*
# Phylogenomic Analysis
A phylogenomic analysis of the HA and NA proteins was done in this study to observe the evolutionary relationship between H17N10 and H18N11 and known evolutionary relationships. Avian HA and NA proteins were utilized for this analysis because avian-species have all known influenza A subtypes besides H17N10 and H18N11 (Olson et al. 2014; “Influenza Type A Viruses” 2017).Another reason avian influenza was used as a model is because most human-infecting influenza A viruses are suspected of having avian origin (Mostafa et al. 2018). Due to this avian-human zoono
  # Phylogenomic analysis of the HA proteins in Influenza A subtypes:
  The phylogenomic analysis of the HA protein begins with downloading and formating the imported data from the ENA database. Due to the quantity of data being downloaded it is essential that the directory is cleared by using the "ls" command. After the directory is clear, the data can be downloaded and formated properly. 
  The following downloaded data is broken down by the HA variables:

       # Download Reference Strains
              #H1N1 (Duck)
                  curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/CCH23215.1?download=true
                  awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CCH23215.1?download=true> H1N1_HA.fa
                  awk '/^>/{print "> H1N1_Duck" ++i; next}{print}' H1N1_HA.fa > header_H1N1_HA.fa
              #H1N2 (Duck)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/APW83915.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'APW83915.1?download=true> H1N2_HA.fa
		   awk '/^>/{print "> H1N2_Duck" ++i; next}{print}' H1N2_HA.fa > header_H1N2_HA.fa
	      #H1N3 (Duck) 
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGH30612.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AGH30612.1?download=true> H1N3_HA.fa
		   awk '/^>/{print "> H1N3_Duck" ++i; next}{print}' H1N3_HA.fa > header_H1N3_HA.fa
	       #H1N4 (Duck)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGR54646.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGR54646.1?download=true>H1N4_HA.fa
		   awk '/^>/{print "> H1N4_Duck" ++i; next}{print}' H1N4_HA.fa > header_H1N4_HA.fa
	       #H1N5 (Duck)
                   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAJ07978.1?download=true
                   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'BAJ07978.1?download=true> H1N5_HA.fa
                   awk '/^>/{print "> H1N5_Duck" ++i; next}{print}' H1N5_HA.fa > header_H1N5_HA.fa
               #H1N6 (Mallard)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADR00746.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'ADR00746.1?download=true> H1N6_HA.fa
		   awk '/^>/{print "> H1N6_Mallard" ++i; next}{print}' H1N6_HA.fa > header_H1N6_HA.fa
	       #H1N7 (ruddy turnstone)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL60569.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AGL60569.1?download=true> H1N7_HA.fa
		   awk '/^>/{print "> H1N7_ruddy_turnstone " ++i; next}{print}' H1N7_HA.fa > header_H1N7_HA.fa
               #H1N8 (mallard)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHL81601.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AHL81601.1?download=true> H1N8_HA.fa
		   awk '/^>/{print "> H1N8_mallard " ++i; next}{print}' H1N8_HA.fa > header_H1N8_HA.fa
               #H1N9 (mallard)
		  curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGG29035.1?download=true
		  awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AGG29035.1?download=true> H1N9_HA.fa
		  awk '/^>/{print "> H1N9_mallard " ++i; next}{print}' H1N9_HA.fa > header_H1N9_HA.fa
	       #H2N1 (duck) 
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN00441.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AHN00441.1?download=true> H2N1_HA.fa
		   awk '/^>/{print "> H2N1_duck " ++i; next}{print}' H2N1_HA.fa > header_H2N1_HA.fa
	       #H2N2 (duck)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIG94040.1?download=true 
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AIG94040.1?download=true> H2N2_HA.fa
		   awk '/^>/{print "> H2N2_duck " ++i; next}{print}' H2N2_HA.fa > header_H2N2_HA.fa
	       #H2N3 (duck)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHZ39487.1?download=true 
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AHZ39487.1?download=true> H2N3_HA.fa
		   awk '/^>/{print "> H2N3_duck " ++i; next}{print}' H2N3_HA.fa > header_H2N3_HA.fa
	       #H2N4 (mallard)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ALZ46891.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'ALZ46891.1?download=true> H2N4_HA.fa
		   awk '/^>/{print "> H2N4_mallard " ++i; next}{print}' H2N4_HA.fa > header_H2N4_HA.fa
		#H2N5 (mallard)
		   curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAT65325.1?download=true
		   awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'AAT65325.1?download=true> H2N5_HA.fa
		   awk '/^>/{print "> H2N5_mallard " ++i; next}{print}' H2N5_HA.fa > header_H2N5_HA.fa
		#H2N6 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ALZ47458.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}'ALZ47458.1?download=true> H2N6_HA.fa
			awk '/^>/{print "> H2N6_mallard " ++i; next}{print}' H2N6_HA.fa > header_H2N6_HA.fa
		#H2N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGR54671.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGR54671.1?download=true > H2N7_HA.fa
			awk '/^>/{print "> H2N7_duck " ++i; next}{print}' H2N7_HA.fa > header_H2N7_HA.fa
		#H2N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL07492.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL07492.1?download=true> H2N8_HA.fa
			awk '/^>/{print "> H2N8_duck " ++i; next}{print}' H2N8_HA.fa > header_H2N8_HA.fa
		#H2N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQS25206.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQS25206.1?download=true > H2N9_HA.fa
			awk '/^>/{print "> H2N9_duck " ++i; next}{print}' H2N9_HA.fa > header_H2N9_HA.fa
		#H3N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ATI21278.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ATI21278.1?download=true > H3N1_HA.fa
			awk '/^>/{print "> H3N1_duck " ++i; next}{print}' H3N1_HA.fa > header_H3N1_HA.fa
		#H3N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJS16375.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJS16375.1?download=true> H3N2_HA.fa
			awk '/^>/{print "> H3N2_duck " ++i; next}{print}' H3N2_HA.fa > header_H3N2_HA.fa
		#H3N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BBC69224.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BBC69224.1?download=true > H3N3_HA.fa
			awk '/^>/{print "> H3N3_duck " ++i; next}{print}' H3N3_HA.fa > header_H3N3_HA.fa
		#H3N4 (duck/ mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB19704.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB19704.1?download=true > H3N4_HA.fa
			awk '/^>/{print "> H3N4_duck_mallard " ++i; next}{print}' H3N4_HA.fa > header_H3N4_HA.fa
		#H3N5 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAL70284.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAL70284.1?download=true > H3N5_HA.fa
			awk '/^>/{print "> H3N5_duck " ++i; next}{print}' H3N5_HA.fa > header_H3N5_HA.fa
		#H3N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHI97157.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHI97157.1?download=true > H3N6_HA.fa
			awk '/^>/{print "> H3N6_duck " ++i; next}{print}' H3N6_HA.fa > header_H3N6_HA.fa
		#H3N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGG83461.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGG83461.1?download=true > H3N7_HA.fa
			awk '/^>/{print "> H3N7_mallard" ++i; next}{print}' H3N7_HA.fa > header_H3N7_HA.fa
		#H3N8 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQS26257.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQS26257.1?download=true > H3N8_HA.fa
			awk '/^>/{print "> H3N8_mallard " ++i; next}{print}' H3N8_HA.fa > header_H3N8_HA.fa
		#H3N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFY06239.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFY06239.1?download=true >H3N9_HA.fa
			awk '/^>/{print "> H3N9_duck " ++i; next}{print}' H3N9_HA.fa > header_H3N9_HA.fa
		#H4N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF46754.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF46754.1?download=true >H4N1_HA.fa
			awk '/^>/{print "> H4N1_duck " ++i; next}{print}' H4N1_HA.fa > header_H4N1_HA.fa
		#H4N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACX55897.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACX55897.1?download=true >H4N2_HA.fa
			awk '/^>/{print "> H4N2_duck " ++i; next}{print}' H4N2_HA.fa > header_H4N2_HA.fa 
		#H4N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ALP45701.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ALP45701.1?download=true >H4N3_HA.fa
			awk '/^>/{print "> H4N3_duck " ++i; next}{print}' H4N3_HA.fa > header_H4N3_HA.fa
		#H4N4 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABI84423.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABI84423.1?download=true >H4N4_HA.fa
			awk '/^>/{print "> H4N4_duck " ++i; next}{print}' H4N4_HA.fa > header_H4N4_HA.fa
		#H4N5 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHM97698.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHM97698.1?download=true >H4N5_HA.fa
			awk '/^>/{print "> H4N5_mallard " ++i; next}{print}' H4N5_HA.fa > header_H4N5_HA.fa
		#H4N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN13689.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN13689.1?download=true >H4N6_HA.fa
			awk '/^>/{print "> H4N6_duck " ++i; next}{print}' H4N6_HA.fa > header_H4N6_HA.fa
		#H4N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACX55888.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACX55888.1?download=true>H4N7_HA.fa
			awk '/^>/{print "> H4N7_duck " ++i; next}{print}' H4N7_HA.fa > header_H4N7_HA.fa
		#H4N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACX55885.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACX55885.1?download=true >H4N8_HA.fa
			awk '/^>/{print "> H4N8_duck " ++i; next}{print}' H4N8_HA.fa > header_H4N8_HA.fa
		#H4N9 (mallard) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHL80167.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHL80167.1?download=true >H4N9_HA.fa
			awk '/^>/{print "> H4N9_mallard " ++i; next}{print}' H4N9_HA.fa > header_H4N9_HA.fa
		#H5N1 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABO64692.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABO64692.1?download=true>H5N1_HA.fa 
			awk '/^>/{print "> H5N1_duck " ++i; next}{print}' H5N1_HA.fa > header_H5N1_HA.fa
		#H5N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ACR09566.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACR09566.1?download=true >H5N2_HA.fa
			awk '/^>/{print "> H5N2_duck " ++i; next}{print}' H5N2_HA.fa > header_H5N2_HA.fa
		#H5N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ACR66926.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACR66926.1?download=true >H5N3_HA.fa
			awk '/^>/{print "> H5N3_duck " ++i; next}{print}' H5N3_HA.fa > header_H5N3_HA.fa
		#H5N4 (mallard)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AMX73132.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AMX73132.1?download=true  >H5N4_HA.fa
			awk '/^>/{print "> H5N4_mallard " ++i; next}{print}' H5N4_HA.fa > header_H5N4_HA.fa
		#H5N5 (duck) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ADD10580.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADD10580.1?download=true  >H5N5_HA.fa
			awk '/^>/{print "> H5N5_duck " ++i; next}{print}' H5N5_HA.fa > header_H5N5_HA.fa
		#H5N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIR93950.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AIR93950.1?download=true >H5N6_HA.fa
			awk '/^>/{print "> H5N6_duck " ++i; next}{print}' H5N6_HA.fa > header_H5N6_HA.fa
		#H5N7 (mallard) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AAT07996.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAT07996.1?download=true  >H5N7_HA.fa
			awk '/^>/{print "> H5N7_mallard " ++i; next}{print}' H5N7_HA.fa > header_H5N7_HA.fa
		#H5N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHI97159.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHI97159.1?download=true >H5N8_HA.fa
			awk '/^>/{print "> H5N8_duck " ++i; next}{print}' H5N8_HA.fa > header_H5N8_HA.fa
		#H5N9(duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGI65009.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGI65009.1?download=true  >H5N9_HA.fa 
			awk '/^>/{print "> H5N9_duck " ++i; next}{print}' H5N9_HA.fa > header_H5N9_HA.fa
		#H6N1 (duck) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABD35522.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABD35522.1?download=true >H6N1_HA.fa
			awk '/^>/{print "> H6N1_duck " ++i; next}{print}' H6N1_HA.fa > header_H6N1_HA.fa
		#H6N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AJM71243.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJM71243.1?download=true >H6N2_HA.fa
			awk '/^>/{print "> H6N2_duck " ++i; next}{print}' H6N2_HA.fa > header_H6N2_HA.fa
		#H6N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABB19184.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB19184.1?download=true > H6N3_HA.fa
			awk '/^>/{print "> H6N3_duck " ++i; next}{print}' H6N3_HA.fa > header_H6N3_HA.fa
		#H6N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/APC32831.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APC32831.1?download=true >H6N4_HA.fa
			awk '/^>/{print "> H6N4_duck " ++i; next}{print}' H6N4_HA.fa > header_H6N4_HA.fa
		#H6N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/APC30385.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APC30385.1?download=true >H6N5_HA.fa
			awk '/^>/{print "> H6N5_duck " ++i; next}{print}' H6N5_HA.fa > header_H6N5_HA.fa
		#H6N6 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AKZ41797.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AKZ41797.1?download=true >H6N6_HA.fa
			awk '/^>/{print "> H6N6_duck " ++i; next}{print}' H6N6_HA.fa > header_H6N6_HA.fa
		#H6N7 (mallard)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGK41573.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK41573.1?download=true >H6N7_HA.fa
			awk '/^>/{print "> H6N7_mallard " ++i; next}{print}' H6N7_HA.fa > header_H6N7_HA.fa
		#H6N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AJM71266.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJM71266.1?download=true >H6N8_HA.fa
			awk '/^>/{print "> H6N8_duck " ++i; next}{print}' H6N8_HA.fa > header_H6N8_HA.fa
		#H6N9 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/CAC84240.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CAC84240.1?download=true >H6N9_HA.fa
			awk '/^>/{print "> H6N9_duck " ++i; next}{print}' H6N9_HA.fa > header_H6N9_HA.fa
		#H7N1 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAF02932.2?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF02932.2?download=true >H7N1_HA.fa
			awk '/^>/{print "> H7N1_duck " ++i; next}{print}' H7N1_HA.fa > header_H7N1_HA.fa
		#H7N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAQ21385.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAQ21385.1?download=true >H7N2_HA.fa
			awk '/^>/{print "> H7N2_duck " ++i; next}{print}' H7N2_HA.fa > header_H7N2_HA.fa
		#H7N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AQS25989.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQS25989.1?download=true >H7N3_HA.fa
			awk '/^>/{print "> H7N3_duck " ++i; next}{print}' H7N3_HA.fa> header_H7N3_HA.fa
		#H7N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGW25713.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGW25713.1?download=true > H7N4_HA.fa
			awk '/^>/{print "> H7N4_duck " ++i; next}{print}' H7N4_HA.fa > header_H7N4_HA.fa
		#H7N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABB87751.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB87751.1?download=true >H7N5_HA.fa
			awk '/^>/{print "> H7N5_duck " ++i; next}{print}' H7N5_HA.fa > header_H7N5_HA.fa
		#H7N6 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AFO83210.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFO83210.1?download=true >H7N6_HA.fa
			awk '/^>/{print "> H7N6_duck " ++i; next}{print}' H7N6_HA.fa > header_H7N6_HA.fa
		#H7N7 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAQ21375.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAQ21375.1?download=true >H7N7_HA.fa
			awk '/^>/{print "> H7N7_duck " ++i; next}{print}' H7N7_HA.fa > header_H7N7_HA.fa
		#H7N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGQ80991.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGQ80991.1?download=true >H7N8_HA.fa
			awk '/^>/{print "> H7N8_duck " ++i; next}{print}' H7N8_HA.fa > header_H7N8_HA.fa
		#H7N9 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGK41573.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK41573.1?download=true >H7N9_HA.fa
			awk '/^>/{print "> H7N9_duck " ++i; next}{print}' H7N9_HA.fa > header_H7N9_HA.fa
		#H8N1 (northern shoveler)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHL82381.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHL82381.1?download=true >H8N1_HA.fa
			awk '/^>/{print "> H8N1_northern_shoveler " ++i; next}{print}' H8N1_HA.fa > header_H8N1_HA.fa
		#H8N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABI85240.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABI85240.1?download=true >H8N2_HA.fa
			awk '/^>/{print "> H8N2_duck " ++i; next}{print}' H8N2_HA.fa > header_H8N2_HA.fa
		#H8N3 (teal) / (Perdix perdix)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ADP07005.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADP07005.1?download=true >H8N3_HA.fa
			awk '/^>/{print "> H8N3_teal " ++i; next}{print}' H8N3_HA.fa > header_H8N3_HA.fa
		#H8N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66275.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66275.1?download=true >H8N4_HA.fa
			awk '/^>/{print "> H8N4_duck " ++i; next}{print}' H8N4_HA.fa > header_H8N4_HA.fa
		#H8N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAL70263.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAL70263.1?download=true >H8N5_HA.fa
			awk '/^>/{print "> H8N5_duck" ++i; next}{print}' H8N5_HA.fa > header_H8N5_HA.fa
		#H8N6 (ruddy shelduck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGU01971.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGU01971.1?download=true >H8N6_HA.fa
			awk '/^>/{print "> H8N6_ruddy_shelduck" ++i; next}{print}' H8N6_HA.fa > header_H8N6_HA.fa
		#H8N7 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66256.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66256.1?download=true >H8N7_HA.fa
			awk '/^>/{print "> H8N7_duck" ++i; next}{print}' H8N7_HA.fa > header_H8N7_HA.fa
		#H8N8 (teal)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AEO22147.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEO22147.1?download=true >H8N8_HA.fa
			awk '/^>/{print "> H8N8_teal" ++i; next}{print}' H8N8_HA.fa > header_H8N8_HA.fa
		#H9N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB20444.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB20444.1?download=true >H9N1_HA.fa
			awk '/^>/{print "> H9N1_duck" ++i; next}{print}' H9N1_HA.fa > header_H9N1_HA.fa
		#H9N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AMP44512.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AMP44512.1?download=true >H9N2_HA.fa
			awk '/^>/{print "> H9N2_duck" ++i; next}{print}' H9N2_HA.fa > header_H9N2_HA.fa
		#H9N3 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF62259.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF62259.1?download=true > H9N3_HA.fa 
			awk '/^>/{print "> H9N3_mallard" ++i; next}{print}' H9N3_HA.fa > header_H9N3_HA.fa 
		#H9N4 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAG69188.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG69188.1?download=true >H9N4_HA.fa
			awk '/^>/{print "> H9N4_duck" ++i; next}{print}' H9N4_HA.fa > header_H9N4_HA.fa
		#H9N5 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AET74791.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AET74791.1?download=true >H9N5_HA.fa
			awk '/^>/{print "> H9N5_ruddy_turnstone" ++i; next}{print}' H9N5_HA.fa > header_H9N5_HA.fa
		#H9N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB20324.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB20324.1?download=true >H9N6_HA.fa
			awk '/^>/{print "> H9N6_duck" ++i; next}{print}' H9N6_HA.fa > header_H9N6_HA.fa
		#H9N7  (/ruddy turnstone) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL58052.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL58052.1?download=true>H9N7_HA.fa
			awk '/^>/{print "> H9N7_ruddy_turnstone" ++i; next}{print}' H9N7_HA.fa> header_H9N7_HA.fa
		#H9N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHA57015.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHA57015.1?download=true >H9N8_HA.fa
			awk '/^>/{print "> H9N8_duck" ++i; next}{print}' H9N8_HA.fa> header_H9N8_HA.fa
		#H9N9 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL58088.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL58088.1?download=true > H9N9_HA.fa
			awk '/^>/{print "> H9N9_ruddy_turnstone" ++i; next}{print}' H9N9_HA.fa > header_H9N9_HA.fa	
		#H10N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF03631.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF03631.1?download=true > H10N1_HA.fa
			awk '/^>/{print "> H10N1_duck " ++i; next}{print}' H10N1_HA.fa > header_H10N1_HA.fa
		#H10N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAU50617.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAU50617.1?download=true > H10N2_HA.fa
			awk '/^>/{print "> H10N2_duck " ++i; next}{print}' H10N2_HA.fa > header_H10N2_HA.fa
		#H10N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAT70789.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAT70789.1?download=true > H10N3_HA.fa
			awk '/^>/{print "> H10N3_duck " ++i; next}{print}' H10N3_HA.fa > header_H10N3_HA.fa
		#H10N4 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHZ39260.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHZ39260.1?download=true > H10N4_HA.fa
			awk '/^>/{print "> H10N4_mallard " ++i; next}{print}' H10N4_HA.fa > header_H10N4_HA.fa
		#H10N5 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJD09831.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJD09831.1?download=true > H10N5_HA.fa
			awk '/^>/{print "> H10N5_duck " ++i; next}{print}' H10N5_HA.fa > header_H10N5_HA.fa
		#H10N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGG83172.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGG83172.1?download=true > H10N6_HA.fa
			awk '/^>/{print "> H10N6_duck " ++i; next}{print}' H10N6_HA.fa > header_H10N6_HA.fa
		#H10N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAT70026.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAT70026.1?download=true> H10N7_HA.fa
			awk '/^>/{print "> H10N7_duck " ++i; next}{print}' H10N7_HA.fa > header_H10N7_HA.fa
		#H10N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJY53778.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJY53778.1?download=true  > H10N8_HA.fa
			awk '/^>/{print "> H10N8_duck " ++i; next}{print}' H10N8_HA.fa > header_H10N8_HA.fa
		#H10N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABI84469.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABI84469.1?download=true > H10N9_HA.fa
			awk '/^>/{print "> H10N9_duck " ++i; next}{print}' H10N9_HA.fa > header_H10N9_HA.fa
		#H11N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66272.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66272.1?download=true > H11N1_HA.fa
			awk '/^>/{print "> H11N1_duck " ++i; next}{print}' H11N1_HA.fa > header_H11N1_HA.fa
		#H11N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAY85533.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAY85533.1?download=true > H11N2_HA.fa
			awk '/^>/{print "> H11N2_duck " ++i; next}{print}' H11N2_HA.fa > header_H11N2_HA.fa
		#H11N3(duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAI68196.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAI68196.1?download=true > H11N3_HA.fa
			awk '/^>/{print "> H11N3_duck " ++i; next}{print}' H11N3_HA.fa > header_H11N3_HA.fa
		#H11N4 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABD91535.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABD91535.1?download=true> H11N4_HA.fa
			awk '/^>/{print "> H11N4_ruddy_turnstone " ++i; next}{print}' H11N4_HA.fa > header_H11N4_HA.fa
		#H11N5 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL59383.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL59383.1?download=true> H11N5_HA.fa
			awk '/^>/{print "> H11N5_ruddy_turnstone " ++i; next}{print}' H11N5_HA.fa > header_H11N5_HA.fa
		#H11N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAA14336.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAA14336.1?download=true > H11N6_HA.fa
			awk '/^>/{print "> H11N6_duck " ++i; next}{print}' H11N6_HA.fa > header_H11N6_HA.fa
		#H11N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADE75071.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADE75071.1?download=true > H11N7_HA.fa
			awk '/^>/{print "> H11N7_mallard " ++i; next}{print}' H11N7_HA.fa > header_H11N7_HA.fa
		#H11N8 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADE75166.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADE75166.1?download=true > H11N8_HA.fa
			awk '/^>/{print "> H11N8_mallard " ++i; next}{print}' H11N8_HA.fa > header_H11N8_HA.fa
		#H11N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAI68200.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAI68200.1?download=true > H11N9_HA.fa
			awk '/^>/{print "> H11N9_duck " ++i; next}{print}' H11N9_HA.fa > header_H11N9_HA.fa
		#12N1 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAM77407.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAM77407.1?download=true > H12N1_HA.fa
			awk '/^>/{print "> H12N1_duck " ++i; next}{print}' H12N1_HA.fa > header_H12N1_HA.fa
		#12N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN04990.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN04990.1?download=true > H12N2_HA.fa
			awk '/^>/{print "> H12N2_duck " ++i; next}{print}' H12N2_HA.fa > header_H12N2_HA.fa
		#12N3 (ruddy shelduck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACV86870.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACV86870.1?download=true > H12N3_HA.fa
			awk '/^>/{print "> H12N3_ruddy_shelduck " ++i; next}{print}' H12N3_HA.fa > header_H12N3_HA.fa
		#12N4 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK41957.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK41957.1?download=true > H12N4_HA.fa
			awk '/^>/{print "> H12N4_mallard " ++i; next}{print}' H12N4_HA.fa > header_H12N4_HA.fa
		#12N5 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF43416.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF43416.1?download=true > H12N5_HA.fa
			awk '/^>/{print "> H12N5_duck " ++i; next}{print}' H12N5_HA.fa > header_H12N5_HA.fa
		#12N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AEB66916.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEB66916.1?download=true> H12N6_HA.fa
			awk '/^>/{print "> H12N6_duck " ++i; next}{print}' H12N6_HA.fa > header_H12N6_HA.fa
		#12N7 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL57633.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL57633.1?download=true >H12N7_HA.fa
			awk '/^>/{print "> H12N7_ruddy_turnstone " ++i; next}{print}' H12N7_HA.fa > header_H12N7_HA.fa
		#12N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK42718.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK42718.1?download=true > H12N8_HA.fa
			awk '/^>/{print "> H12N8_duck " ++i; next}{print}' H12N8_HA.fa > header_H12N8_HA.fa
		#12N9 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AMQ29561.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AMQ29561.1?download=true >H12N9_HA.fa
			awk '/^>/{print "> H12N9_mallard " ++i; next}{print}' H12N9_HA.fa > header_H12N9_HA.fa
		#13N1 (laughing gull) HA only
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGW82819.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGW82819.1?download=true > H13N1_HA.fa
			awk '/^>/{print "> H13N1_laughing_gull " ++i; next}{print}' H13N1_HA.fa > header_H13N1_HA.fa
		#13N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAN14686.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAN14686.1?download=true > H13N2_HA.fa
			awk '/^>/{print "> H13N2_duck" ++i; next}{print}' H13N2_HA.fa > header_H13N2_HA.fa
		#13N3 (laughing gull)/ Black headed gull
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGW82808.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGW82808.1?download=true > H13N3_HA.fa
			awk '/^>/{print "> H13N3_gull" ++i; next}{print}' H13N3_HA.fa > header_H13N3_HA.fa
		#13N4 (red Knot) HA only
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGW82822.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGW82822.1?download=true > H13N4_HA.fa
			awk '/^>/{print "> H13N4_red_knot " ++i; next}{print}' H13N4_HA.fa > header_H13N4_HA.fa
		#13N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF38383.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF38383.1?download=true> H13N6_HA.fa
			awk '/^>/{print "> H13N6_duck" ++i; next}{print}' H13N6_HA.fa > header_H13N6_HA.fa
		#13N8 (blackheaded gull)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/APC32409.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APC32409.1?download=true > H13N8_HA.fa
			awk '/^>/{print "> H13N8_gull" ++i; next}{print}' H13N8_HA.fa > header_H13N8_HA.fa
		#13N9 (laughing gull) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK42180.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK42180.1?download=true > H13N9_HA.fa
			awk '/^>/{print "> H13N9_gull" ++i; next}{print}' H13N9_HA.fa > header_H13N9_HA.fa
		#14N2 (northern shoveler)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGO03619.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGO03619.1?download=true > H14N2_HA.fa
			awk '/^>/{print "> H14N2_northern_shoveler " ++i; next}{print}' H14N2_HA.fa > header_H14N2_HA.fa
		#14N3 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHJ57334.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHJ57334.1?download=true > H14N3_HA.fa
			awk '/^>/{print "> H14N3_teal" ++i; next}{print}' H14N3_HA.fa > header_H14N3_HA.fa
		#14N4 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQY18287.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY18287.1?download=true > H14N4_HA.fa
			awk '/^>/{print "> H14N4_teal" ++i; next}{print}' H14N4_HA.fa > header_H14N4_HA.fa
		#14N5 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGB51323.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGB51323.1?download=true > H14N5_HA.fa
			awk '/^>/{print "> H14N5_mallard " ++i; next}{print}' H14N5_HA.fa > header_H14N5_HA.fa
		#14N6 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AEP68847.2?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEP68847.2?download=true > H14N6_HA.fa
			awk '/^>/{print "> H14N6_duck " ++i; next}{print}' H14N6_HA.fa > header_H14N6_HA.fa
		#14N7 (blue-winged teal/)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ANA11343.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ANA11343.1?download=true > H14N7_HA.fa
			awk '/^>/{print "> H14N7_teal " ++i; next}{print}' H14N7_HA.fa > header_H14N7_HA.fa
		#14N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGE07966.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGE07966.1?download=true > H14N8_HA.fa
			awk '/^>/{print "> H14N8_duck " ++i; next}{print}' H14N8_HA.fa > header_H14N8_HA.fa
		#15N2 (Australian shelduck)- NO NA
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB90704.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB90704.1?download=true > H15N2_HA.fa		
			awk '/^>/{print "> H15N2_Australian_shelduck " ++i; next}{print}' H15N2_HA.fa > header_H15N2_HA.fa
		#15N4 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AEO31332.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEO31332.1?download=true > H15N4_HA.fa
			awk '/^>/{print "> H15N4_teal " ++i; next}{print}' H15N4_HA.fa > header_H15N4_HA.fa
		#15N6 (shearwater) – No NA
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACZ48521.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACZ48521.1?download=true > H15N6_HA.fa		
			awk '/^>/{print "> H15N6_shearwater " ++i; next}{print}' H15N6_HA.fa >  header_H15N6_HA.fa;/
		#15N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIY68624.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AIY68624.1?download=true > H15N7_HA.fa
			awk '/^>/{print "> H15N7_mallard " ++i; next}{print}' H15N7_HA.fa > header_H15N7_HA.fa
		#15N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF48363.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF48363.1?download=true > H15N8_HA.fa
			awk '/^>/{print "> H15N8_duck " ++i; next}{print}' H15N8_HA.fa > header_H15N8_HA.fa
		#15N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQY17922.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY17922.1?download=true > H15N9_HA.fa
			awk '/^>/{print "> H15N9_duck " ++i; next}{print}' H15N9_HA.fa > header_H15N9_HA.fa
		#H16N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAO94331.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAO94331.1?download=true > H16N3_HA.fa
			awk '/^>/{print "> H16N3_duck " ++i; next}{print}' H16N3_HA.fa > header_H16N3_HA.fa
		#H16N9 (gull)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK24021.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK24021.1?download=true > H16N9_HA.fa
			awk '/^>/{print "> H16N9_gull " ++i; next}{print}' H16N9_HA.fa > header_H16N9_HA.fa
		# Downloaded H17N10 HA
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ CY103892.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CY103892.1?download=true >H17N10_HA.fasta
			awk '/^>/{print "> H17N10_bat_" ++i; next}{print}' H17N10_HA.fasta > header_H17N10_HA.fa
		# Downloaded   H18N11 hemagglutinin (HA) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/CY125945.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CY125945.1?download=true > H18N11_HA.fasta
			awk '/^>/{print "> H18N11_bat_" ++i; next}{print}' H18N11_HA.fasta > header_H18N11_HA.fa
Once all of the data has been downloaded and formated, its important to combine the Fasta files: 
		
		cat header_H1N1_HA.fa header_H1N2_HA.fa header_H1N3_HA.fa header_H1N4_HA.fa header_H1N5_HA.fa header_H1N6_HA.fa header_H1N7_HA.fa header_H1N8_HA.fa header_H1N9_HA.fa header_H2N1_HA.fa header_H2N2_HA.fa header_H2N3_HA.fa header_H2N4_HA.fa header_H2N5_HA.fa header_H2N6_HA.fa header_H2N7_HA.fa header_H2N8_HA.fa header_H2N9_HA.fa header_H3N1_HA.fa header_H3N2_HA.fa header_H3N3_HA.fa header_H3N4_HA.fa header_H3N5_HA.fa header_H3N6_HA.fa header_H3N7_HA.fa header_H3N8_HA.fa header_H3N9_HA.fa header_H4N1_HA.fa header_H4N2_HA.fa header_H4N3_HA.fa header_H4N4_HA.fa header_H4N5_HA.fa header_H4N6_HA.fa header_H4N7_HA.fa header_H4N8_HA.fa header_H4N9_HA.fa header_H5N1_HA.fa header_H5N2_HA.fa header_H5N3_HA.fa header_H5N4_HA.fa header_H5N5_HA.fa header_H5N6_HA.fa header_H5N7_HA.fa header_H5N8_HA.fa header_H5N9_HA.fa header_H6N1_HA.fa header_H6N2_HA.fa header_H6N3_HA.fa header_H6N4_HA.fa header_H6N5_HA.fa header_H6N6_HA.fa header_H6N7_HA.fa header_H6N8_HA.fa header_H6N9_HA.fa header_H7N1_HA.fa header_H7N2_HA.fa header_H7N3_HA.fa header_H7N4_HA.fa header_H7N5_HA.fa header_H7N6_HA.fa header_H7N7_HA.fa header_H7N8_HA.fa header_H7N9_HA.fa header_H8N1_HA.fa header_H8N2_HA.fa header_H8N3_HA.fa header_H8N4_HA.fa header_H8N5_HA.fa header_H8N6_HA.fa header_H8N7_HA.fa header_H8N8_HA.fa header_H9N1_HA.fa header_H9N2_HA.fa header_H9N3_HA.fa header_H9N4_HA.fa header_H9N5_HA.fa header_H9N6_HA.fa header_H9N7_HA.fa header_H9N8_HA.fa header_H9N9_HA.fa header_H10N1_HA.fa header_H10N2_HA.fa header_H10N3_HA.fa header_H10N4_HA.fa header_H10N5_HA.fa header_H10N6_HA.fa header_H10N7_HA.fa header_H10N8_HA.fa header_H10N9_HA.fa header_H11N1_HA.fa header_H11N2_HA.fa header_H11N3_HA.fa header_H11N4_HA.fa header_H11N5_HA.fa header_H11N6_HA.fa header_H11N7_HA.fa header_H11N8_HA.fa header_H11N9_HA.fa header_H12N1_HA.fa header_H12N2_HA.fa header_H12N3_HA.fa header_H12N4_HA.fa header_H12N5_HA.fa header_H12N6_HA.fa header_H12N7_HA.fa header_H12N8_HA.fa header_H12N9_HA.fa header_H13N1_HA.fa header_H13N2_HA.fa header_H13N3_HA.fa header_H13N4_HA.fa header_H13N6_HA.fa header_H13N8_HA.fa header_H13N9_HA.fa header_H14N2_HA.fa header_H14N3_HA.fa header_H14N4_HA.fa header_H14N5_HA.fa header_H14N6_HA.fa header_H14N7_HA.fa header_H14N8_HA.fa header_H15N2_HA.fa header_H15N4_HA.fa header_H15N6_HA.fa header_H15N7_HA.fa header_H15N8_HA.fa header_H15N9_HA.fa header_H16N3_HA.fa header_H16N9_HA.fa header_H18N11_HA.fa header_H17N10_HA.fa > Influenza_HA_Phylogenetics_Tree.fa

After combining the files, a MAFFT analysis is done to align the sequences.

		mafft --auto Influenza_HA_Phylogenetics_Tree.fa > Output_Influenza_HA_phylogenic.fa

 "--auto" precedes the input file, which output file of our previous "cat" command
 "Output_Influenza_HA_phylogenic.fa" is the name of our output file in our study, but any output file name will work as long as the syntax is correct.
 
 
The ouput from the MAFFT sequence alignment is then used to build a phylogenic tree based on our data:

		iqtree -s Output_Influenza_HA_phylogenic.fa -m JC -bb 1000 -pre output
"-s" precedes our input file which is the output file of our MAFFT alignment
"JC" is the model that was used for this study
"-bb" is the boostraping subset used for this study was 1000
"-pre" precedes the name of our output file. I used "output" as the file name for simplicity sake, but the output file name could be anything.

The iqtree should produce a file named: output.contree.
This file was then "cat"ed onto the terminal"

		cat output.contree
This should be the viewed result of the "cat" command:
			
			(H1N1_Duck1:0.037485,(((H1N2_Duck1:0.018950,H1N4_Duck1:0.009877)100:0.018579 (H1N3_Duck1:0.044272,H1N5_Duck1:0.020226)61:0.014080)100:0.059193,(((((H2N1_duck:0.025917,H2N5_mallard:0.011109)99:0.014810,((H2N4_mallard:0.017297,H2N6_mallard:0.011822)98:0.007558,H2N9_duck:0.030154)51:0.015007)100:0.067918,(((H2N2_duck:0.034788,H2N3_duck:0.019467)100:0.013951,H2N8_duck:0.033609)100:0.020480,H2N7_duck:0.048236)100:0.055911)100:0.126212,((((H5N1_duck:0.021438,(H5N5_duck:0.004871,H5N6_duck:0.043724)100:0.027708)100:0.048773,(H5N7_mallard:0.011607,H5N8_duck:0.035641)96:0.010873)83:0.013520,H5N3_duck:0.018210)100:0.088744,((H5N2_duck:0.004405,H5N4_mallard:0.014071)100:0.013677,H5N9_duck:0.021921)100:0.060745)100:0.129553)99:0.077207,((((((((H3N1_duck:0.062937,(H3N2_duck:0.045816,((H3N3_duck:0.006348,H3N6_duck:0.013856)100:0.008662,H3N5_duck:0.014017)99:0.012673)100:0.034303)100:0.034012,(((H3N4_duck_mallard:0.004135,H3N8_mallard:0.028226)99:0.005049,H3N7_mallard1:0.027320)99:0.017091,H3N9_duck:0.035972)100:0.058009)100:0.197910,((((H4N1_duck:0.043805,(H4N3_duck:0.058759,(H4N7_duck:0.014758,H4N8_duck:0.015192)100:0.018921)100:0.019741)100:0.028527,(H4N6_duck:0.021703,H4N9_mallard:0.017650)100:0.041274)100:0.055672,((H4N2_duck:0.049087,H4N5_mallard:0.051582)97:0.022793,H4N4_duck:0.037716)100:0.066405)100:0.093841,(((((H14N2_northern_shoveler:0.003535,H14N7_teal:0.028108)84:0.002341,H14N3_teal1:0.006484)81:0.000154,H14N4_teal1:0.011658)100:0.014949,(H14N6_duck:0.000002,H14N8_duck:0.000002)100:0.013499)100:0.044174,H14N5_mallard:0.061645)100:0.190541)100:0.084285)100:0.178559,(((((H7N1_duck:0.010640,(H7N6_duck:0.023578,(H7N7_duck:0.010082,H7N8_duck:0.003688)100:0.009002)98:0.016765)98:0.020511,(H7N2_duck:0.012151,H7N4_duck:0.011955)100:0.033086)100:0.107610,(H7N3_duck:0.054217,H7N5_duck:0.048384)100:0.111900)100:0.072002,(((H15N2_Australian_shelduck:0.000580,H15N6_shearwater:0.010730)100:0.006489,H15N8_duck:0.022112)100:0.053239,(H15N4_teal:0.012108,(H15N7_mallard:0.005143,H15N9_duck:0.017917)100:0.016883)100:0.044125)100:0.112851)100:0.124484,(((H10N1_duck:0.074411,H10N9_duck:0.031277)96:0.030517,(((((H10N2_duck:0.000594,H10N3_duck:0.000593)100:0.008498,H10N7_duck:0.005244)99:0.001153,H10N5_duck:0.004320)100:0.025656,H10N8_duck:0.008263)100:0.009734,H10N4_mallard:0.017786)100:0.038952)100:0.078477,H10N6_duck:0.090791)100:0.182031)100:0.144418)100:0.180854,((((H8N1_northern_shoveler:0.034284,((H8N2_duck:0.000002,H8N7_duck1:0.000588)100:0.023862,H8N3_teal:0.054044)71:0.015634)100:0.048945,(H8N4_duck:0.035441,(H8N5_duck1:0.018984,(H8N6_ruddy_shelduck1:0.016962,H8N8_teal1:0.018347)100:0.013607)100:0.038655)100:0.047581)100:0.192474,((H12N1_duck:0.040553,H12N3_ruddy_shelduck:0.036918)100:0.077937,((((H12N2_duck:0.015421,H12N6_duck:0.016580)100:0.012834,H12N5_duck:0.010553)100:0.015592,H12N7_ruddy_turnstone:0.032968)100:0.024622,((H12N4_mallard:0.007745,H12N8_duck:0.002936)100:0.011397,H12N9_mallard:0.008326)99:0.018178)100:0.076679)100:0.164890)99:0.080732,((((H9N1_duck1:0.026489,H9N6_duck1:0.020397)93:0.007848,((H9N3_mallard1:0.016953,H9N4_duck1:0.040012)98:0.010195,(H9N7_ruddy_turnstone1:0.000002,H9N9_ruddy_turnstone1:0.002379)100:0.041929)99:0.022122)92:0.017434,H9N5_ruddy_turnstone1:0.059888)97:0.026694,(H9N2_duck1:0.085229,H9N8_duck1:0.068415)99:0.029750)100:0.214060)100:0.112215)66:0.034903,((((H11N1_duck:0.041273,H11N6_duck:0.043805)99:0.016937,((H11N2_duck:0.026992,(H11N7_mallard:0.004692,H11N8_mallard:0.007755)100:0.015854)100:0.021043,(H11N3_duck:0.011217,H11N9_duck:0.021875)100:0.057382)91:0.019824)100:0.075334,(H11N4_ruddy_turnstone:0.050684,H11N5_ruddy_turnstone:0.044200)100:0.069906)100:0.165333,(((((H13N1_laughing_gull:0.003019,H13N4_red_knot:0.011145)94:0.009497,H13N3_gull1:0.012099)100:0.068211,(H13N8_gull1:0.073126,H13N9_gull1:0.074574)100:0.054576)100:0.059404,(H13N2_duck1:0.035346,H13N6_duck1:0.026080)100:0.111890)100:0.066996,(H16N3_duck:0.011153,H16N9_gull:0.016094)100:0.157349)100:0.173587)100:0.100840)87:0.058775,(H18N11_bat_1:0.235617,H17N10_bat_1:0.277448)100:0.192995)94:0.067707,(((((H6N1_duck:0.016929,H6N9_duck:0.016120)100:0.020274,(H6N2_duck:0.018050,H6N5_duck:0.017267)100:0.018429)98:0.013608,(H6N4_duck:0.016847,H6N8_duck:0.014486)100:0.020877)99:0.035875,H6N6_duck:0.090490)100:0.082523,(H6N3_duck:0.029735,(H6N7_mallard:0.000002,H7N9_duck:0.000002)100:0.029759)100:0.108224)100:0.185574)81:0.048781)100:0.198332)99:0.034306,((H1N6_Mallard1:0.010596,H1N7_ruddy_turnstone:0.025355)97:0.008724,(H1N8_mallard:0.009585,H1N9_mallard:0.011207)98:0.007144)100:0.039323);
  The result of the "cat" command was then copied and pasted into  FigTree v1.4.4.

![Influenza HA phylogenic tree](https://github.com/eeg1025g71120/InfluenzaProjectRepo/blob/master/Screenshot_2020-05-12%20InfluenzaHA_avian_phylo_compares.png)
	*A nicer version is available to view at: 
		![Influenza phylogenic tree HA](https://github.com/eeg1025g71120/InfluenzaProjectRepo/blob/master/HA%20Protein%20Influenza%20Phylogenomic%20Tree.pdf)
 
  # Phylogenomic analysis of the NA protein in Influenza A subtypes:
  The phylogenomic analysis of the NA protein, again begins with downloading and formating the imported data from the ENA database. Due to the quantity of data being downloaded it is essential that we clear the directory from the previous tree This can be done using the "ls" command. After the directory is clear, the data can be downloaded and formated properly. 
  The following downloaded data is broken down by the HA variables:
  
  	# Download Reference Strains
		#H1N1 (Duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAF77038.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAF77038.1?download=true > H1N1_NA.fa
			awk '/^>/{print "> H1N1_Duck" ++i; next}{print}' H1N1_NA.fa > header_H1N1_NA.fa
		#H1N2 (Duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ARQ84282.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ARQ84282.1?download=true > H1N2_NA.fa
			awk '/^>/{print "> H1N2_Duck" ++i; next}{print}' H1N2_NA.fa > header_H1N2_NA.fa
		#H1N3 (Duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB20430.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB20430.1?download=true > H1N3_NA.fa
			awk '/^>/{print "> H1N3_Duck" ++i; next}{print}' H1N3_NA.fa > header_H1N3_NA.fa
		#H1N4 (Duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ALR82579.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ALR82579.1?download=true > H1N4_NA.fa
			awk '/^>/{print "> H1N4_Duck" ++i; next}{print}' H1N4_NA.fa > header_H1N4_NA.fa
		#H1N5 (Duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAJ07979.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAJ07979.1?download=true > H1N5_NA.fa
			awk '/^>/{print "> H1N5_Duck" ++i; next}{print}' H1N5_NA.fa > header_H1N5_NA.fa
		#H1N6 (Mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAO62069.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAO62069.1?download=true > H1N6_NA.fa
			awk '/^>/{print "> H1N6_Mallard" ++i; next}{print}' H1N6_NA.fa > header_H1N6_NA.fa
		#H1N7 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL60427.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL60427.1?download=true > H1N7_NA.fa
			awk '/^>/{print "> H1N7_ruddy_turnstone " ++i; next}{print}' H1N7_NA.fa > header_H1N7_NA.fa
		#H1N8 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHL81604.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHL81604.1?download=true > H1N8_NA.fa
			awk '/^>/{print "> H1N8_mallard " ++i; next}{print}' H1N8_NA.fa > header_H1N8_NA.fa
		#H1N9 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGG29038.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGG29038.1?download=true true > H1N9_NA.fa
			awk '/^>/{print "> H1N9_mallard " ++i; next}{print}' H1N9_NA.fa > header_H1N9_NA.fa
		#H2N1 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN00444.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN00444.1?download=true > H2N1_NA.fa
			awk '/^>/{print "> H2N1_duck " ++i; next}{print}' H2N1_NA.fa > header_H2N1_NA.fa
		#H2N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF34378.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF34378.1?download=true > H2N2_NA.fa
			awk '/^>/{print "> H2N2_duck " ++i; next}{print}' H2N2_NA.fa > header_H2N2_NA.fa
		#H2N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB17706.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB17706.1?download=true > H2N3_NA.fa
			awk '/^>/{print "> H2N3_duck " ++i; next}{print}' H2N3_NA.fa > header_H2N3_NA.fa
		#H2N4 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB18072.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB18072.1?download=true > H2N4_NA.fa
			awk '/^>/{print "> H2N4_mallard " ++i; next}{print}' H2N4_NA.fa > header_H2N4_NA.fa
		#H2N5 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB18028.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB18028.1?download=true > H2N5_NA.fa
			awk '/^>/{print "> H2N5_mallard " ++i; next}{print}' H2N5_NA.fa > header_H2N5_NA.fa
		#H2N6 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFJ13218.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFJ13218.1?download=true > H2N6_NA.fa
			awk '/^>/{print "> H2N6_mallard " ++i; next}{print}' H2N6_NA.fa > header_H2N6_NA.fa
		#H2N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGR54666.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGR54666.1?download=true> H2N7_NA.fa
			awk '/^>/{print "> H2N7_duck " ++i; next}{print}' H2N7_NA.fa > header_H2N7_NA.fa
		#H2N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFJ13273.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFJ13273.1?download=true> H2N8_NA.fa
			awk '/^>/{print "> H2N8_duck " ++i; next}{print}' H2N8_NA.fa > header_H2N8_NA.fa
		#H2N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB20168.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB20168.1?download=true > H2N9_NA.fa
			awk '/^>/{print "> H2N9_duck " ++i; next}{print}' H2N9_NA.fa > header_H2N9_NA.fa
		#H3N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AAO62060.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAO62060.1?download=true > H3N1_NA.fa
			awk '/^>/{print "> H3N1_duck " ++i; next}{print}' H3N1_NA.fa > header_H3N1_NA.fa
		#H3N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAL70287.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAL70287.1?download=true  > H3N2_NA.fa
			awk '/^>/{print "> H3N2_duck " ++i; next}{print}' H3N2_NA.fa > header_H3N2_NA.fa
		#H3N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFM08987.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFM08987.1?download=true > H3N3_NA.fa
			awk '/^>/{print "> H3N3_duck " ++i; next}{print}' H3N3_NA.fa > header_H3N3_NA.fa
		#H3N4 ( mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACT84630.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACT84630.1?download=true > H3N4_NA.fa
			awk '/^>/{print "> H3N4_duck_mallard " ++i; next}{print}' H3N4_NA.fa > header_H3N4_NA.fa
		#H3N5 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAL70285.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAL70285.1?download=true > H3N5_NA.fa
			awk '/^>/{print "> H3N5_duck " ++i; next}{print}' H3N5_NA.fa > header_H3N5_NA.fa
		#H3N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHI97151.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHI97151.1?download=true > H3N6_NA.fa
			awk '/^>/{print "> H3N6_duck " ++i; next}{print}' H3N6_NA.fa > header_H3N6_NA.fa
		#H3N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGG83464.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGG83464.1?download=true > H3N7_NA.fa
			awk '/^>/{print "> H3N7_mallard" ++i; next}{print}' H3N7_NA.fa > header_H3N7_NA.fa
		#H3N8 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACZ45080.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACZ45080.1?download=true > H3N8_NA.fa
			awk '/^>/{print "> H3N8_mallard " ++i; next}{print}' H3N8_NA.fa > header_H3N8_NA.fa
		#H3N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGQ81968.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGQ81968.1?download=true >H3N9_NA.fasta
			awk '/^>/{print "> H3N9_duck " ++i; next}{print}' H3N9_NA.fa > header_H3N9_NA.fa
		#H4N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF46755.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF46755.1?download=true >H4N1_NA.fa
			awk '/^>/{print "> H4N1_duck " ++i; next}{print}' H4N1_NA.fa > header_H4N1_NA.fa
		#H4N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB87564.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB87564.1?download=true >H4N2_NA.fa
			awk '/^>/{print "> H4N2_duck " ++i; next}{print}' H4N2_NA.fa > header_H4N2_NA.fa 
		#H4N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66268.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66268.1?download=true >H4N3_NA.fa
			awk '/^>/{print "> H4N3_duck " ++i; next}{print}' H4N3_NA.fa > header_H4N3_NA.fa
		#H4N4 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB87597.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB87597.1?download=true >H4N4_NA.fa
			awk '/^>/{print "> H4N4_duck " ++i; next}{print}' H4N4_NA.fa > header_H4N4_NA.fa
		#H4N5 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHM97701.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHM97701.1?download=true true >H4N5_NA.fa
			awk '/^>/{print "> H4N5_mallard " ++i; next}{print}' H4N5_NA.fa > header_H4N5_NA.fa
		#H4N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHI97154.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHI97154.1?download=true >H4N6_NA.fa
			awk '/^>/{print "> H4N6_duck " ++i; next}{print}' H4N6_NA.fa > header_H4N6_NA.fa
		#H4N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF43459.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF43459.1?download=true  >H4N7_NA.fa
			awk '/^>/{print "> H4N7_duck " ++i; next}{print}' H4N7_NA.fa > header_H4N7_NA.fa
		#H4N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAH69255.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAH69255.1?download=true >H4N8_NA.fa
			awk '/^>/{print "> H4N8_duck " ++i; next}{print}' H4N8_NA.fa > header_H4N8_NA.fa
		#H4N9 (mallard) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHL77825.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHL77825.1?download=true >H4N9_NA.fa
			awk '/^>/{print "> H4N9_mallard " ++i; next}{print}' H4N9_NA.fa > header_H4N9_NA.fa
		#H5N1 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABA55722.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABA55722.1?download=true >H5N1_NA.fa 
			awk '/^>/{print "> H5N1_duck " ++i; next}{print}' H5N1_NA.fa > header_H5N1_NA.fa
		#H5N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAF49410.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF49410.1?download=true >H5N2_NA.fa
			awk '/^>/{print "> H5N2_duck " ++i; next}{print}' H5N2_NA.fa > header_H5N2_NA.fa
		#H5N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/CAH61340.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CAH61340.1?download=true >H5N3_NA.fa
			awk '/^>/{print "> H5N3_duck " ++i; next}{print}' H5N3_NA.fa > header_H5N3_NA.fa
		#H5N4 (mallard)
			curl -LO   https://www.ebi.ac.uk/ena/browser/api/fasta/AMX73135.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AMX73135.1?download=true >H5N4_NA.fa
			awk '/^>/{print "> H5N4_mallard " ++i; next}{print}' H5N4_NA.fa > header_H5N4_NA.fa
		#H5N5 (duck) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ADD10582.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADD10582.1?download=true >H5N5_NA.fa
			awk '/^>/{print "> H5N5_duck " ++i; next}{print}' H5N5_NA.fa > header_H5N5_NA.fa
		#H5N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/APG39713.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APG39713.1?download=true >H5N6_NA.fa
			awk '/^>/{print "> H5N6_duck " ++i; next}{print}' H5N6_NA.fa > header_H5N6_NA.fa
		#H5N7 (mallard) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AAT07997.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AAT07997.1?download=true >H5N7_NA.fa
			awk '/^>/{print "> H5N7_mallard " ++i; next}{print}' H5N7_NA.fa > header_H5N7_NA.fa
		#H5N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHM24061.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHM24061.1?download=true > H5N8_NA.fa
			awk '/^>/{print "> H5N8_duck " ++i; next}{print}' H5N8_NA.fa > header_H5N8_NA.fa
		#H5N9(duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGI65011.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGI65011.1?download=true >H5N9_NA.fa 
			awk '/^>/{print "> H5N9_duck " ++i; next}{print}' H5N9_NA.fa > header_H5N9_NA.fa
		#H6N1 (duck) 
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAG85127.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG85127.1?download=true >H6N1_NA.fa
			awk '/^>/{print "> H6N1_duck " ++i; next}{print}' H6N1_NA.fa > header_H6N1_NA.fa
		#H6N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ATY73654.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ATY73654.1?download=true >H6N2_NA.fa
			awk '/^>/{print "> H6N2_duck " ++i; next}{print}' H6N2_NA.fa > header_H6N2_NA.fa
		#H6N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABB19231.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB19231.1?download=true > H6N3_NA.fa
			awk '/^>/{print "> H6N3_duck " ++i; next}{print}' H6N3_NA.fa > header_H6N3_NA.fa
		#H6N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/APC32520.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APC32520.1?download=true >H6N4_NA.fa
			awk '/^>/{print "> H6N4_duck " ++i; next}{print}' H6N4_NA.fa > header_H6N4_NA.fa
		#H6N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AJM71275.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJM71275.1?download=true >H6N5_NA.fa
			awk '/^>/{print "> H6N5_duck " ++i; next}{print}' H6N5_NA.fa > header_H6N5_NA.fa
		#H6N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFF27250.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFF27250.1?download=true >H6N6_NA.fa
			awk '/^>/{print "> H6N6_duck " ++i; next}{print}' H6N6_NA.fa > header_H6N6_NA.fa
		#H6N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK41576.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK41576.1?download=true >H6N7_NA.fa
			awk '/^>/{print "> H6N7_mallard " ++i; next}{print}' H6N7_NA.fa > header_H6N7_NA.fa
		#H6N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/CAM91994.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CAM91994.1?download=true >H6N8_NA.fa
			awk '/^>/{print "> H6N8_duck " ++i; next}{print}' H6N8_NA.fa > header_H6N8_NA.fa
		#H6N9 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHN03576.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN03576.1?download=true >H6N9_NA.fa
			awk '/^>/{print "> H6N9_duck " ++i; next}{print}' H6N9_NA.fa > header_H6N9_NA.fa
		#H7N1 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AQY17885.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY17885.1?download=true>H7N1_NA.fa
			awk '/^>/{print "> H7N1_duck " ++i; next}{print}' H7N1_NA.fa > header_H7N1_NA.fa
		#H7N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ACC61824.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACC61824.1?download=true >H7N2_NA.fa
			awk '/^>/{print "> H7N2_duck " ++i; next}{print}' H7N2_NA.fa > header_H7N2_NA.fa
		#H7N3 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAH69248.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAH69248.1?download=true > H7N3_NA.fa
			awk '/^>/{print "> H7N3_duck " ++i; next}{print}' H7N3_NA.fa> header_H7N3_NA.fa
		#H7N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AFO83143.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFO83143.1?download=true > H7N4_NA.fa
			awk '/^>/{print "> H7N4_duck " ++i; next}{print}' H7N4_NA.fa > header_H7N4_NA.fa
		#H7N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ABB87754.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB87754.1?download=true >H7N5_NA.fa
			awk '/^>/{print "> H7N5_duck " ++i; next}{print}' H7N5_NA.fa > header_H7N5_NA.fa
		#H7N6 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AFO83163.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFO83163.1?download=true > H7N6_NA.fa
			awk '/^>/{print "> H7N6_duck " ++i; next}{print}' H7N6_NA.fa > header_H7N6_NA.fa
		#H7N7 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAN37427.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAN37427.1?download=true >H7N7_NA.fa
			awk '/^>/{print "> H7N7_duck " ++i; next}{print}' H7N7_NA.fa > header_H7N7_NA.fa
		#H7N8 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGQ81930.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGQ81930.1?download=true >H7N8_NA.fa
			awk '/^>/{print "> H7N8_duck " ++i; next}{print}' H7N8_NA.fa > header_H7N8_NA.fa
		#H7N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AKM15216.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AKM15216.1?download=true >H7N9_NA.fa
			awk '/^>/{print "> H7N9_duck " ++i; next}{print}' H7N9_NA.fa > header_H7N9_NA.fa
		#H8N1 (northern shoveler)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AHL82384.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHL82384.1?download=true >H8N1_NA.fa
			awk '/^>/{print "> H8N1_northern_shoveler " ++i; next}{print}' H8N1_NA.fa > header_H8N1_NA.fa
		#H8N2 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAQ54175.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAQ54175.1?download=true >H8N2_NA.fa
			awk '/^>/{print "> H8N2_duck " ++i; next}{print}' H8N2_NA.fa > header_H8N2_NA.fa
		#H8N3  (Perdix perdix)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/CAP69840.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CAP69840.1?download=true > H8N3_NA.fa
			awk '/^>/{print "> H8N3_perdix_perdix " ++i; next}{print}' H8N3_NA.fa > header_H8N3_NA.fa
		#H8N4 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/ACA04722.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACA04722.1?download=true >H8N4_NA.fa
			awk '/^>/{print "> H8N4_duck " ++i; next}{print}' H8N4_NA.fa > header_H8N4_NA.fa
		#H8N5 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAH69251.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAH69251.1?download=true >H8N5_NA.fa
			awk '/^>/{print "> H8N5_duck" ++i; next}{print}' H8N5_NA.fa > header_H8N5_NA.fa
		#H8N6 (ruddy shelduck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AGY42064.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGY42064.1?download=true >H8N6_NA.fa
			awk '/^>/{print "> H8N6_ruddy_shelduck" ++i; next}{print}' H8N6_NA.fa > header_H8N6_NA.fa
		#H8N7 (duck)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66257.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66257.1?download=true  >H8N7_NA.fa
			awk '/^>/{print "> H8N7_duck" ++i; next}{print}' H8N7_NA.fa > header_H8N7_NA.fa
		#H8N8 (teal)
			curl -LO  https://www.ebi.ac.uk/ena/browser/api/fasta/AEO22149.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEO22149.1?download=true >H8N8_NA.fa
			awk '/^>/{print "> H8N8_teal" ++i; next}{print}' H8N8_NA.fa > header_H8N8_NA.fa
		#H9N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB19696.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB19696.1?download=true >H9N1_NA.fa
			awk '/^>/{print "> H9N1_duck" ++i; next}{print}' H9N1_NA.fa > header_H9N1_NA.fa
		#H9N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/QDP68602.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' QDP68602.1?download=true >H9N2_NA.fa
			awk '/^>/{print "> H9N2_duck" ++i; next}{print}' H9N2_NA.fa > header_H9N2_NA.fa
		#H9N3 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/CAH61341.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' CAH61341.1?download=true > H9N3_NA.fa 
			awk '/^>/{print "> H9N3_mallard" ++i; next}{print}' H9N3_NA.fa > header_H9N3_NA.fa 
		#H9N4 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAG69189.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG69189.1?download=true >H9N4_NA.fa
			awk '/^>/{print "> H9N4_duck" ++i; next}{print}' H9N4_NA.fa > header_H9N4_NA.fa
		#H9N5 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AET74794.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AET74794.1?download=true >H9N5_NA.fa
			awk '/^>/{print "> H9N5_ruddy_turnstone" ++i; next}{print}' H9N5_NA.fa > header_H9N5_NA.fa
		#H9N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB20327.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB20327.1?download=true >H9N6_NA.fa
			awk '/^>/{print "> H9N6_duck" ++i; next}{print}' H9N6_NA.fa > header_H9N6_NA.fa
		#H9N7  (ruddy turnstone) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL58055.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL58055.1?download=true >H9N7_NA.fa
			awk '/^>/{print "> H9N7_ruddy_turnstone" ++i; next}{print}' H9N7_NA.fa> header_H9N7_NA.fa
		#H9N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHA57007.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHA57007.1?download=true >H9N8_NA.fa
			awk '/^>/{print "> H9N8_duck" ++i; next}{print}' H9N8_NA.fa> header_H9N8_NA.fa
		#H9N9 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AET74921.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AET74921.1?download=true > H9N9_NA.fa
			awk '/^>/{print "> H9N9_ruddy_turnstone" ++i; next}{print}' H9N9_NA.fa > header_H9N9_NA.fa
		#H10N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF03632.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF03632.1?download=true> H10N1_NA.fa
			awk '/^>/{print "> H10N1_duck " ++i; next}{print}' H10N1_NA.fa > header_H10N1_NA.fa
		#H10N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAN04626.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAN04626.1?download=true > H10N2_NA.fa
			awk '/^>/{print "> H10N2_duck " ++i; next}{print}' H10N2_NA.fa > header_H10N2_NA.fa
		#H10N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACA04652.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACA04652.1?download=true > H10N3_NA.fa
			awk '/^>/{print "> H10N3_duck " ++i; next}{print}' H10N3_NA.fa > header_H10N3_NA.fa
		#H10N4 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHZ37592.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHZ37592.1?download=true> H10N4_NA.fa
			awk '/^>/{print "> H10N4_mallard " ++i; next}{print}' H10N4_NA.fa > header_H10N4_NA.fa
		#H10N5 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF03532.2?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF03532.2?download=true > H10N5_NA.fa
			awk '/^>/{print "> H10N5_duck " ++i; next}{print}' H10N5_NA.fa > header_H10N5_NA.fa
		#H10N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB87981.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB87981.1?download=true > H10N6_NA.fa
			awk '/^>/{print "> H10N6_duck " ++i; next}{print}' H10N6_NA.fa > header_H10N6_NA.fa
		#H10N7 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF48646.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF48646.1?download=true > H10N7_NA.fa
			awk '/^>/{print "> H10N7_duck " ++i; next}{print}' H10N7_NA.fa > header_H10N7_NA.fa
		#H10N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AJY53781.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AJY53781.1?download=true > H10N8_NA.fa
			awk '/^>/{print "> H10N8_duck " ++i; next}{print}' H10N8_NA.fa > header_H10N8_NA.fa
		#H10N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF47128.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF47128.1?download=true > H10N9_NA.fa
			awk '/^>/{print "> H10N9_duck " ++i; next}{print}' H10N9_NA.fa > header_H10N9_NA.fa
		#H11N1 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAG66273.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAG66273.1?download=true > H11N1_NA.fa
			awk '/^>/{print "> H11N1_duck " ++i; next}{print}' H11N1_NA.fa > header_H11N1_NA.fa
		#H11N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACA04671.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACA04671.1?download=true > H11N2_NA.fa
			awk '/^>/{print "> H11N2_duck " ++i; next}{print}' H11N2_NA.fa > header_H11N2_NA.fa
		#H11N3(duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGE83705.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGE83705.1?download=true > H11N3_NA.fa
			awk '/^>/{print "> H11N3_duck " ++i; next}{print}' H11N3_NA.fa > header_H11N3_NA.fa
		#H11N4 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AXB34989.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AXB34989.1?download=true  > H11N4_NA.fa
			awk '/^>/{print "> H11N4_ruddy_turnstone " ++i; next}{print}' H11N4_NA.fa > header_H11N4_NA.fa
		#H11N5 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADP07897.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADP07897.1?download=true > H11N5_NA.fa
			awk '/^>/{print "> H11N5_teal " ++i; next}{print}' H11N5_NA.fa > header_H11N5_NA.fa
		#H11N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN13651.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN13651.1?download=true > H11N6_NA.fa
			awk '/^>/{print "> H11N6_duck " ++i; next}{print}' H11N6_NA.fa > header_H11N6_NA.fa
		#H11N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADE75073.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADE75073.1?download=true > H11N7_NA.fa
			awk '/^>/{print "> H11N7_mallard " ++i; next}{print}' H11N7_NA.fa > header_H11N7_NA.fa
		#H11N8 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADE75168.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADE75168.1?download=true > H11N8_NA.fa
			awk '/^>/{print "> H11N8_mallard " ++i; next}{print}' H11N8_NA.fa > header_H11N8_NA.fa
		#H11N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AHN13695.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AHN13695.1?download=true > H11N9_NA.fa
			awk '/^>/{print "> H11N9_duck " ++i; next}{print}' H11N9_NA.fa > header_H11N9_NA.fa
		#H12N1 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BBB38857.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BBB38857.1?download=true > H12N1_NA.fa
			awk '/^>/{print "> H12N1_duck " ++i; next}{print}' H12N1_NA.fa > header_H12N1_NA.fa
		#H12N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/QBJ05810.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' QBJ05810.1?download=true > H12N2_NA.fa
			awk '/^>/{print "> H12N2_duck " ++i; next}{print}' H12N2_NA.fa > header_H12N2_NA.fa
		#H12N3 (ruddy shelduck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ACV86873.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ACV86873.1?download=true > H12N3_NA.fa
			awk '/^>/{print "> H12N3_ruddy_shelduck " ++i; next}{print}' H12N3_NA.fa > header_H12N3_NA.fa
		#H12N4 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK41960.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK41960.1?download=true > H12N4_NA.fa
			awk '/^>/{print "> H12N4_mallard " ++i; next}{print}' H12N4_NA.fa > header_H12N4_NA.fa
		#H12N5 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB19465.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB19465.1?download=true > H12N5_NA.fa
			awk '/^>/{print "> H12N5_duck " ++i; next}{print}' H12N5_NA.fa > header_H12N5_NA.fa
		#H12N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AEB66919.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEB66919.1?download=true > H12N6_NA.fa
			awk '/^>/{print "> H12N6_duck " ++i; next}{print}' H12N6_NA.fa > header_H12N6_NA.fa
		#H12N7 (ruddy turnstone)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGL57624.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGL57624.1?download=true > H12N7_NA.fa
			awk '/^>/{print "> H12N7_ruddy_turnstone " ++i; next}{print}' H12N7_NA.fa > header_H12N7_NA.fa
		#H12N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK42721.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK42721.1?download=true > H12N8_HA.fa
			awk '/^>/{print "> H12N8_duck " ++i; next}{print}' H12N8_HA.fa > header_H12N8_HA.fa
		#H12N9 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AMQ46820.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AMQ46820.1?download=true >H12N9_NA.fa
			awk '/^>/{print "> H12N9_mallard " ++i; next}{print}' H12N9_NA.fa > header_H12N9_NA.fa
		#H13N2 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAN14687.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAN14687.1?download=true > H13N2_NA.fa
			awk '/^>/{print "> H13N2_duck" ++i; next}{print}' H13N2_NA.fa > header_H13N2_NA.fa
		#H13N3 Black headed gull
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/APC32395.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' APC32395.1?download=true> H13N3_NA.fa
			awk '/^>/{print "> H13N3_gull" ++i; next}{print}' H13N3_NA.fa > header_H13N3_NA.fa
		#H13N6 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAF38385.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAF38385.1?download=true > H13N6_NA.fa
			awk '/^>/{print "> H13N6_duck" ++i; next}{print}' H13N6_NA.fa > header_H13N6_NA.fa
		#H13N8 (blackheaded gull)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ADQ26643.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ADQ26643.1?download=true> H13N8_NA.fa
			awk '/^>/{print "> H13N8_gull" ++i; next}{print}' H13N8_NA.fa > header_H13N8_NA.fa
		#H13N9 (laughing gull) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK42183.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK42183.1?download=true> H13N9_NA.fa
			awk '/^>/{print "> H13N9_gull" ++i; next}{print}' H13N9_NA.fa > header_H13N9_NA.fa
		#H14N2 (northern shoveler)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGO03622.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGO03622.1?download=true > H14N2_NA.fa
			awk '/^>/{print "> H14N2_northern_shoveler " ++i; next}{print}' H14N2_NA.fa > header_H14N2_NA.fa
		#H14N3 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQY18228.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY18228.1?download=true > H14N3_NA.fa
			awk '/^>/{print "> H14N3_teal" ++i; next}{print}' H14N3_NA.fa > header_H14N3_NA.fa
		#H14N4 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQY18492.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY18492.1?download=true > H14N4_NA.fa
			awk '/^>/{print "> H14N4_teal" ++i; next}{print}' H14N4_NA.fa > header_H14N4_NA.fa
		#H14N5 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGB51326.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGB51326.1?download=true > H14N5_NA.fa
			awk '/^>/{print "> H14N5_mallard " ++i; next}{print}' H14N5_NA.fa > header_H14N5_NA.fa
		#H14N6 (duck) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFX81883.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFX81883.1?download=true > H14N6_NA.fa
			awk '/^>/{print "> H14N6_duck " ++i; next}{print}' H14N6_NA.fa > header_H14N6_NA.fa
		#H14N7 (blue-winged teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ANA11345.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ANA11345.1?download=true > H14N7_NA.fa
			awk '/^>/{print "> H14N7_teal " ++i; next}{print}' H14N7_NA.fa > header_H14N7_NA.fa
		#H14N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGE07969.1?download=true 
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGE07969.1?download=true > H14N8_NA.fa
			awk '/^>/{print "> H14N8_duck " ++i; next}{print}' H14N8_NA.fa > header_H14N8_NA.fa
		#H15N4 (teal)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AEO31334.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AEO31334.1?download=true > H15N4_NA.fa
			awk '/^>/{print "> H15N4_teal " ++i; next}{print}' H15N4_NA.fa > header_H15N4_NA.fa
		#H15N7 (mallard)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AIY68625.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AIY68625.1?download=true > H15N7_NA.fa
			awk '/^>/{print "> H15N7_mallard " ++i; next}{print}' H15N7_NA.fa > header_H15N7_NA.fa
		#H15N8 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/ABB88133.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' ABB88133.1?download=true > H15N8_NA.fa
			awk '/^>/{print "> H15N8_duck " ++i; next}{print}' H15N8_NA.fa > header_H15N8_NA.fa
		#H15N9 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AQY17663.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AQY17663.1?download=true > H15N9_NA.fa
			awk '/^>/{print "> H15N9_duck " ++i; next}{print}' H15N9_NA.fa > header_H15N9_NA.fa
		#H16N3 (duck)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/BAO94333.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' BAO94333.1?download=true > H16N3_NA.fa
			awk '/^>/{print "> H16N3_duck " ++i; next}{print}' H16N3_NA.fa > header_H16N3_NA.fa
		#H16N9 (gull)
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGK24023.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGK24023.1?download=true > H16N9_NA.fa
			awk '/^>/{print "> H16N9_gull " ++i; next}{print}' H16N9_NA.fa > header_H16N9_NA.fa
		# Downloaded H17N10 NA
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AFC35430.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AFC35430.1?download=true >H17N10_NA.fasta
			awk '/^>/{print "> H17N10_bat_" ++i; next}{print}' H17N10_NA.fasta > header_H17N10_NA.fa
		# Downloaded   H18N11 hemagglutinin (NA) 
			curl -LO https://www.ebi.ac.uk/ena/browser/api/fasta/AGX84936.1?download=true
			awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' AGX84936.1?download=true > H18N11_NA.fasta
			awk '/^>/{print "> H18N11_bat_" ++i; next}{print}' H18N11_NA.fasta > header_H18N11_NA.fa
Again, the downloaded and formated data is combined into a Fasta files: 

	cat header_H1N1_NA.fa header_H1N2_NA.fa header_H1N3_NA.fa header_H1N4_NA.fa header_H1N5_NA.fa header_H1N6_NA.fa header_H1N7_NA.fa header_H1N8_NA.fa header_H1N9_NA.fa header_H2N1_NA.fa header_H2N2_NA.fa header_H2N3_NA.fa header_H2N4_NA.fa header_H2N5_NA.fa header_H2N6_NA.fa header_H2N7_NA.fa header_H2N8_NA.fa header_H2N9_NA.fa header_H3N1_NA.fa header_H3N2_NA.fa header_H3N3_NA.fa header_H3N4_NA.fa header_H3N5_NA.fa header_H3N6_NA.fa header_H3N7_NA.fa header_H3N8_NA.fa header_H3N9_NA.fa header_H4N1_NA.fa header_H4N2_NA.fa header_H4N3_NA.fa header_H4N4_NA.fa header_H4N5_NA.fa header_H4N6_NA.fa header_H4N7_NA.fa header_H4N8_NA.fa header_H4N9_NA.fa header_H5N1_NA.fa header_H5N2_NA.fa header_H5N3_NA.fa header_H5N4_NA.fa header_H5N5_NA.fa header_H5N6_NA.fa header_H5N7_NA.fa header_H5N8_NA.fa header_H5N9_NA.fa header_H6N1_NA.fa header_H6N2_NA.fa header_H6N3_NA.fa header_H6N4_NA.fa header_H6N5_NA.fa header_H6N6_NA.fa header_H6N7_NA.fa header_H6N8_NA.fa header_H6N9_NA.fa header_H7N1_NA.fa header_H7N2_NA.fa header_H7N3_NA.fa header_H7N4_NA.fa header_H7N5_NA.fa header_H7N6_NA.fa header_H7N7_NA.fa header_H7N8_NA.fa header_H7N9_NA.fa header_H8N1_NA.fa header_H8N2_NA.fa header_H8N3_NA.fa header_H8N4_NA.fa header_H8N5_NA.fa header_H8N6_NA.fa header_H8N7_NA.fa header_H8N8_NA.fa header_H9N1_NA.fa header_H9N2_NA.fa header_H9N3_NA.fa header_H9N4_NA.fa header_H9N5_NA.fa header_H9N6_NA.fa header_H9N7_NA.fa header_H9N8_NA.fa header_H9N9_NA.fa header_H10N1_NA.fa header_H10N2_NA.fa header_H10N3_NA.fa header_H10N4_NA.fa header_H10N5_NA.fa header_H10N6_NA.fa header_H10N7_NA.fa header_H10N8_NA.fa header_H10N9_NA.fa header_H11N1_NA.fa header_H11N2_NA.fa header_H11N3_NA.fa header_H11N4_NA.fa header_H11N5_NA.fa header_H11N6_NA.fa header_H11N7_NA.fa header_H11N8_NA.fa header_H11N9_NA.fa header_H12N1_NA.fa header_H12N2_NA.fa header_H12N3_NA.fa header_H12N4_NA.fa header_H12N5_NA.fa header_H12N6_NA.fa header_H12N7_NA.fa header_H12N8_HA.fa header_H12N9_NA.fa header_H13N2_NA.fa header_H13N3_NA.fa header_H13N6_NA.fa header_H13N8_NA.fa header_H13N9_NA.fa header_H14N2_NA.fa header_H14N3_NA.fa header_H14N4_NA.fa header_H14N5_NA.fa header_H14N6_NA.fa header_H14N7_NA.fa header_H14N8_NA.fa header_H15N4_NA.fa header_H15N7_NA.fa header_H15N8_NA.fa header_H15N9_NA.fa header_H16N3_NA.fa header_H16N9_NA.fa header_H17N10_NA.fa header_H18N11_NA.fa> Influenza_NA_Phylogenetics_Tree.fa


After combining the files, another MAFFT analysis is done to align the sequences:

	mafft --auto Influenza_NA_Phylogenetics_Tree.fa > Output_Influenza_NA_Phylogenetics_Tree.fa
 "--auto" precedes the input file, which output file of our previous "cat" command
 "Output_Influenza_HA_phylogenic.fa" is the name of our output file in our study, but any output file name will work as long as the syntax is correct.
	
The ouput from the MAFFT sequence alignment is then used to build a phylogenic tree based on our data:	
	
	iqtree -s Output_Influenza_NA_Phylogenetics_Tree.fa -m JC -bb 1000 -pre output
"-s" precedes our input file which is the output file of our MAFFT alignment
"JC" is the model that was used for this study
"-bb" is the boostraping subset used for this study was 1000
"-pre" precedes the name of our output file. I used "output" as the file name for simplicity sake, but the output file name could be anything.

The iqtree should then produce a file named: output.contree (same as last time).
This file was then "cat"ed onto the terminal"

		cat output.contree
This should be the viewed result of the "cat" command:


	(H1N1_Duck1:0.019219,(((((((((((H1N2_Duck1:0.057968,H9N2_duck1:0.078540)90:0.030822,(((H2N2_duck:0.021279,(H4N2_duck:0.023570,H6N2_duck:0.058247)88:0.020280)83:0.007679,H14N2_northern_shoveler:0.036362)78:0.009658,((((H3N2_duck:0.007801,((H8N2_duck:0.002110,H12N2_duck:0.005008)100:0.005728,H13N2_duck1:0.016557)100:0.000720)100:0.015640,H10N2_duck:0.014602)100:0.015887,H7N2_duck:0.026506)100:0.015147,(H5N2_duck:0.017092,H11N2_duck:0.025908)100:0.021769)100:0.020640)95:0.027314)100:0.312195,(((((H1N6_Mallard1:0.015236,H12N6_duck:0.020447)100:0.018054,(H2N6_mallard:0.025784,H10N6_duck:0.008862)100:0.021312)100:0.094131,(((((((H3N6_duck:0.002127,H4N6_duck:0.004264)100:0.003462,H14N6_duck:0.007934)95:0.000771,(H7N6_duck:0.003481,H11N6_duck:0.019469)99:0.002949)100:0.036013,H8N6_ruddy_shelduck1:0.034684)93:0.013801,H5N6_duck:0.105655)92:0.016189,H9N6_duck1:0.032256)99:0.043545,H13N6_duck1:0.069666)100:0.071585)100:0.159908,(((((H1N9_mallard:0.036030,(H13N9_gull1:0.001650,H16N9_gull:0.005345)100:0.046378)69:0.004634,(H5N9_duck:0.025348,H12N9_mallard:0.018278)96:0.007605)100:0.022493,(H6N9_duck:0.011805,H9N9_ruddy_turnstone1:0.028542)75:0.008088)100:0.027368,(H2N9_duck:0.011599,(H4N9_mallard:0.008760,(H7N9_duck:0.022528,(H11N9_duck:0.038676,H15N9_duck:0.022681)100:0.004869)100:0.007940)100:0.003404)100:0.034195)100:0.071257,H10N9_duck:0.093902)100:0.166420)100:0.094297,((((H1N7_ruddy_turnstone:0.008671,H14N7_teal:0.018609)100:0.009063,(((H6N7_mallard:0.002843,H9N7_ruddy_turnstone1:0.015756)54:0.000712,H12N7_ruddy_turnstone:0.005675)47:0.000594,H8N7_duck1:0.036419)72:0.020508)71:0.010458,H3N7_mallard1:0.019871)100:0.137163,(H2N7_duck:0.026894,(((H4N7_duck:0.009929,(H7N7_duck:0.015757,H15N7_mallard:0.034749)99:0.002867)98:0.002156,H5N7_mallard:0.017099)99:0.003054,(H10N7_duck:0.014699,H11N7_mallard:0.027837)100:0.010687)100:0.022937)100:0.103085)100:0.191505)100:0.101169)99:0.081854,(((H1N3_Duck1:0.051502,(H3N3_duck:0.048185,((((H4N3_duck:0.023001,H12N3_ruddy_shelduck:0.021977)98:0.003678,H8N3_perdix_perdix:0.015060)92:0.002647,((H5N3_duck:0.011142,H9N3_mallard1:0.008195)100:0.002065,H10N3_duck:0.014759)100:0.012388)88:0.001563,H7N3_duck:0.023733)94:0.009826)100:0.041446)99:0.035398,(((H2N3_duck:0.007353,H6N3_duck:0.012712)78:0.013527,H14N3_teal1:0.035787)75:0.014112,H11N3_duck:0.024529)100:0.036237)100:0.101595,(H13N3_gull1:0.017792,H16N3_duck:0.017168)100:0.169100)100:0.237524)100:0.135411,(H17N10_bat_1:0.486560,H18N11_bat_1:0.428456)100:0.265770)87:0.033546,((((((H1N5_Duck1:0.009400,H3N5_duck:0.016308)100:0.015277,H5N5_duck:0.024859)92:0.014117,(H6N5_duck:0.030470,(H8N5_duck1:0.005646,H10N5_duck:0.000721)100:0.012789)98:0.008420)90:0.023225,H14N5_mallard:0.029820)100:0.104033,(((H2N5_mallard:0.023261,((H7N5_duck:0.020817,H12N5_duck:0.009912)96:0.010150,H9N5_ruddy_turnstone1:0.020889)96:0.020515)89:0.010595,H11N5_teal:0.031420)89:0.011104,H4N5_mallard:0.027769)100:0.085317)100:0.170421,((((((H1N8_mallard:0.035529,(H3N8_mallard:0.010627,H12N8_duck:0.013161)100:0.013535)87:0.004060,(H4N8_duck:0.017589,H9N8_duck1:0.025086)100:0.014865)84:0.007079,H14N8_duck:0.039688)91:0.013620,H2N8_duck:0.043427)91:0.023521,H15N8_duck:0.045200)100:0.083700,(H5N8_duck:0.063881,(((H6N8_duck:0.012706,((H8N8_teal1:0.013386,H11N8_mallard:0.008080)90:0.000734,H10N8_duck:0.027127)90:0.003923)100:0.032906,H7N8_duck:0.050912)98:0.018883,H13N8_gull1:0.080364)53:0.020233)100:0.102109)100:0.130067)100:0.180178)100:0.090388,((((H1N4_Duck1:0.013555,H7N4_duck:0.017614)100:0.013270,(H8N4_duck:0.010402,H9N4_duck1:0.007795)99:0.004210)100:0.018829,((H6N4_duck:0.015715,H15N4_teal:0.002166)99:0.027084,H10N4_mallard:0.014462)82:0.015979)100:0.060701,((H2N4_mallard:0.018108,(H3N4_duck_mallard:0.010426,((H5N4_mallard:0.018618,H14N4_teal1:0.016445)91:0.003852,H12N4_mallard:0.005571)91:0.002842)100:0.031116)100:0.019255,H4N4_duck:0.019014)100:0.070600)100:0.180005)100:0.219678,H3N1_duck:0.037364)86:0.028782,((((H5N1_duck:0.041495,H6N1_duck:0.031157)99:0.010191,(H7N1_duck:0.029772,H12N1_duck:0.019143)100:0.033181)100:0.042167,H10N1_duck:0.021305)87:0.021066,H11N1_duck:0.022421)88:0.023535)100:0.041679,H4N1_duck:0.021062)96:0.007955,((H8N1_northern_shoveler:0.044138,H11N4_ruddy_turnstone:0.021693)100:0.025476,H9N1_duck1:0.010526)99:0.007362)99:0.004719,H2N1_duck:0.017001);


 The result of the "cat" command was then copied and pasted into  FigTree v1.4.4.

![Influenza NA phylogenic tree](https://github.com/eeg1025g71120/InfluenzaProjectRepo/blob/master/Screenshot_2020-05-12%20InfluenzaHA_avian_phylo_compares.png)
	*A nicer, more detailed version is available to view at: 
		![Influenza phylogenic tree NA](https://github.com/eeg1025g71120/InfluenzaProjectRepo/blob/master/Influenza_NA_phylogenomics)
			
The two analyses show that H17N10 and H18N11 HA and NA proteins are different compared to the HA and NA proteins of human-infecting influenza virus. However, it should be noted that the phylogenomic analysis found that H17N10 and H18N11 share a common ancestor with avian H3 and N2 proteins. The H3 and N2 protein subtypes have been associated with the zoonotic transfer of disease from avian speices into humans(Guan et al 2019). This association indicates that there is potential for the H17N10 and H18N11 to undergo antigenic shift, and thus has the potential to become zoonotic


#Work Cited:
Guan, L., Shi, J., Kong, X., Ma, S., Zhang, Y., Yin, X., He, X., Liu, L., Suzuki, Y., Li, C., Deng, G., & Chen, H. (2019). H3N2 avian influenza viruses detected in live poultry markets in China bind to human-type receptors and transmit in guinea pigs and ferrets. Emerging microbes & infections, 8(1), 1280–1290. https://doi.org/10.1080/22221751.2019.1660590
Influenza Type A Viruses. (2017, April 19). Retrieved from https://www.cdc.gov/flu/avianflu/influenza-a-virus-subtypes.htm
Mostafa, A., Abdelwhab, E. M., Mettenleiter, T. C., & Pleschka, S. (2018). Zoonotic Potential of Influenza A Viruses: A Comprehensive Overview. Viruses, 10(9), 497. https://doi.org/10.3390/v10090497
Olson, S. H., Parmley, J., Soos, C., Gilbert, M., Latorre-Margalef, N., Hall, J. S., Hansbro, P. M., Leighton, F., Munster, V., & Joly, D. (2014). Sampling strategies and biodiversity of influenza A subtypes in wild birds. PloS one, 9(3), e90826. https://doi.org/10.1371/journal.pone.0090826
