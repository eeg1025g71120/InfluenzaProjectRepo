# InfluenzaProjectRepo
  This is the repository being used for my project on human succeptibility to bat influenza.
 	mkdir Influenza_Analysis
 	cd  Influenza_Analysis
# Blast Analysis of H17N10's HA protein
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
    #Combine Human Influenza Strains
            cat H1N1_HA.fasta H2N2_HA.fasta H3N2_HA.fasta H5N1_HA.fasta > Human_Influenza_Viruses.fasta
    # BLAST
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
        blastp -db influenza -max_target_seqs 1 -query H17H10_HA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
      # view BLAST
          less blast.out
     # remove all of the blast files with rm
# Blast Analysis of H18N11's HA protein
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
    #Combine Human Influenza Strains
            cat H1N1_HA.fasta H2N2_HA.fasta H3N2_HA.fasta H5N1_HA.fasta > Human_Influenza_Viruses.fasta
     # BLAST
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
        blastp -db influenza -max_target_seqs 1 -query H18H11_HA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
     # view BLAST
          less blast.out
     # remove all of the blast files with rm
     
     
# Blast Analysis of H17N10's NA protein
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
     #Combine Human Influenza Strains
            cat H1N1_NA.fasta H2N2_NA.fasta H3N2_NA.fasta H5N1_NA.fasta > Human_Influenza_Viruses.fasta
     # BLAST
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
        blastp -db influenza -max_target_seqs 1 -query H17H10_NA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
     # view BLAST
          less blast.out
     # remove all of the blast files with rm
    
    
    
# Blast Analysis of H18N11's NA protein
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
     #Combine Human Influenza Strains
            cat H1N1_NA.fasta H2N2_NA.fasta H3N2_NA.fasta H5N1_NA.fasta > Human_Influenza_Viruses.fasta
     # BLAST
        makeblastdb -in Human_Influenza_Viruses.fasta -out influenza -dbtype prot
        blastp -db influenza -max_target_seqs 1 -query H18H11_NA.fasta -outfmt '6 qseqid qlen length pident gaps evalue stitle' -evalue 1e-10 -num_threads 6 -out blast.out
     # view BLAST
          less blast.out
     # remove all of the blast files with rm
  # Phylogenomic analysis of the HA proteins in Influenza A subtypes:
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
Combine the downloaded files: 
		
		cat header_H1N1_HA.fa header_H1N2_HA.fa header_H1N3_HA.fa header_H1N4_HA.fa header_H1N5_HA.fa header_H1N6_HA.fa header_H1N7_HA.fa header_H1N8_HA.fa header_H1N9_HA.fa header_H2N1_HA.fa header_H2N2_HA.fa header_H2N3_HA.fa header_H2N4_HA.fa header_H2N5_HA.fa header_H2N6_HA.fa header_H2N7_HA.fa header_H2N8_HA.fa header_H2N9_HA.fa header_H3N1_HA.fa header_H3N2_HA.fa header_H3N3_HA.fa header_H3N4_HA.fa header_H3N5_HA.fa header_H3N6_HA.fa header_H3N7_HA.fa header_H3N8_HA.fa header_H3N9_HA.fa header_H4N1_HA.fa header_H4N2_HA.fa header_H4N3_HA.fa header_H4N4_HA.fa header_H4N5_HA.fa header_H4N6_HA.fa header_H4N7_HA.fa header_H4N8_HA.fa header_H4N9_HA.fa header_H5N1_HA.fa header_H5N2_HA.fa header_H5N3_HA.fa header_H5N4_HA.fa header_H5N5_HA.fa header_H5N6_HA.fa header_H5N7_HA.fa header_H5N8_HA.fa header_H5N9_HA.fa header_H6N1_HA.fa header_H6N2_HA.fa header_H6N3_HA.fa header_H6N4_HA.fa header_H6N5_HA.fa header_H6N6_HA.fa header_H6N7_HA.fa header_H6N8_HA.fa header_H6N9_HA.fa header_H7N1_HA.fa header_H7N2_HA.fa header_H7N3_HA.fa header_H7N4_HA.fa header_H7N5_HA.fa header_H7N6_HA.fa header_H7N7_HA.fa header_H7N8_HA.fa header_H7N9_HA.fa header_H8N1_HA.fa header_H8N2_HA.fa header_H8N3_HA.fa header_H8N4_HA.fa header_H8N5_HA.fa header_H8N6_HA.fa header_H8N7_HA.fa header_H8N8_HA.fa header_H9N1_HA.fa header_H9N2_HA.fa header_H9N3_HA.fa header_H9N4_HA.fa header_H9N5_HA.fa header_H9N6_HA.fa header_H9N7_HA.fa header_H9N8_HA.fa header_H9N9_HA.fa header_H10N1_HA.fa header_H10N2_HA.fa header_H10N3_HA.fa header_H10N4_HA.fa header_H10N5_HA.fa header_H10N6_HA.fa header_H10N7_HA.fa header_H10N8_HA.fa header_H10N9_HA.fa header_H11N1_HA.fa header_H11N2_HA.fa header_H11N3_HA.fa header_H11N4_HA.fa header_H11N5_HA.fa header_H11N6_HA.fa header_H11N7_HA.fa header_H11N8_HA.fa header_H11N9_HA.fa header_H12N1_HA.fa header_H12N2_HA.fa header_H12N3_HA.fa header_H12N4_HA.fa header_H12N5_HA.fa header_H12N6_HA.fa header_H12N7_HA.fa header_H12N8_HA.fa header_H12N9_HA.fa header_H13N1_HA.fa header_H13N2_HA.fa header_H13N3_HA.fa header_H13N4_HA.fa header_H13N6_HA.fa header_H13N8_HA.fa header_H13N9_HA.fa header_H14N2_HA.fa header_H14N3_HA.fa header_H14N4_HA.fa header_H14N5_HA.fa header_H14N6_HA.fa header_H14N7_HA.fa header_H14N8_HA.fa header_H15N2_HA.fa header_H15N4_HA.fa header_H15N6_HA.fa header_H15N7_HA.fa header_H15N8_HA.fa header_H15N9_HA.fa header_H16N3_HA.fa header_H16N9_HA.fa header_H18N11_HA.fa header_H17N10_HA.fa > Influenza_HA_Phylogenetics_Tree.fa

		mafft --auto Influenza_HA_Phylogenetics_Tree.fa > Output_Influenza_HA_phylogenic.fa

		iqtree -s Output_Influenza_HA_phylogenic.fa -m JC -bb 1000 -pre output

		cat output.contree

  # Phylogenomic analysis of the NA protein in Influenza A subtypes:
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

	cat header_H1N1_NA.fa header_H1N2_NA.fa header_H1N3_NA.fa header_H1N4_NA.fa header_H1N5_NA.fa header_H1N6_NA.fa header_H1N7_NA.fa header_H1N8_NA.fa header_H1N9_NA.fa header_H2N1_NA.fa header_H2N2_NA.fa header_H2N3_NA.fa header_H2N4_NA.fa header_H2N5_NA.fa header_H2N6_NA.fa header_H2N7_NA.fa header_H2N8_NA.fa header_H2N9_NA.fa header_H3N1_NA.fa header_H3N2_NA.fa header_H3N3_NA.fa header_H3N4_NA.fa header_H3N5_NA.fa header_H3N6_NA.fa header_H3N7_NA.fa header_H3N8_NA.fa header_H3N9_NA.fa header_H4N1_NA.fa header_H4N2_NA.fa header_H4N3_NA.fa header_H4N4_NA.fa header_H4N5_NA.fa header_H4N6_NA.fa header_H4N7_NA.fa header_H4N8_NA.fa header_H4N9_NA.fa header_H5N1_NA.fa header_H5N2_NA.fa header_H5N3_NA.fa header_H5N4_NA.fa header_H5N5_NA.fa header_H5N6_NA.fa header_H5N7_NA.fa header_H5N8_NA.fa header_H5N9_NA.fa header_H6N1_NA.fa header_H6N2_NA.fa header_H6N3_NA.fa header_H6N4_NA.fa header_H6N5_NA.fa header_H6N6_NA.fa header_H6N7_NA.fa header_H6N8_NA.fa header_H6N9_NA.fa header_H7N1_NA.fa header_H7N2_NA.fa header_H7N3_NA.fa header_H7N4_NA.fa header_H7N5_NA.fa header_H7N6_NA.fa header_H7N7_NA.fa header_H7N8_NA.fa header_H7N9_NA.fa header_H8N1_NA.fa header_H8N2_NA.fa header_H8N3_NA.fa header_H8N4_NA.fa header_H8N5_NA.fa header_H8N6_NA.fa header_H8N7_NA.fa header_H8N8_NA.fa header_H9N1_NA.fa header_H9N2_NA.fa header_H9N3_NA.fa header_H9N4_NA.fa header_H9N5_NA.fa header_H9N6_NA.fa header_H9N7_NA.fa header_H9N8_NA.fa header_H9N9_NA.fa header_H10N1_NA.fa header_H10N2_NA.fa header_H10N3_NA.fa header_H10N4_NA.fa header_H10N5_NA.fa header_H10N6_NA.fa header_H10N7_NA.fa header_H10N8_NA.fa header_H10N9_NA.fa header_H11N1_NA.fa header_H11N2_NA.fa header_H11N3_NA.fa header_H11N4_NA.fa header_H11N5_NA.fa header_H11N6_NA.fa header_H11N7_NA.fa header_H11N8_NA.fa header_H11N9_NA.fa header_H12N1_NA.fa header_H12N2_NA.fa header_H12N3_NA.fa header_H12N4_NA.fa header_H12N5_NA.fa header_H12N6_NA.fa header_H12N7_NA.fa header_H12N8_HA.fa header_H12N9_NA.fa header_H13N2_NA.fa header_H13N3_NA.fa header_H13N6_NA.fa header_H13N8_NA.fa header_H13N9_NA.fa header_H14N2_NA.fa header_H14N3_NA.fa header_H14N4_NA.fa header_H14N5_NA.fa header_H14N6_NA.fa header_H14N7_NA.fa header_H14N8_NA.fa header_H15N4_NA.fa header_H15N7_NA.fa header_H15N8_NA.fa header_H15N9_NA.fa header_H16N3_NA.fa header_H16N9_NA.fa header_H17N10_NA.fa header_H18N11_NA.fa> Influenza_NA_Phylogenetics_Tree.fa

	mafft --auto Influenza_NA_Phylogenetics_Tree.fa > Output_Influenza_NA_Phylogenetics_Tree.fa

	iqtree -s Output_Influenza_NA_Phylogenetics_Tree.fa -m JC -bb 1000 -pre output
	 cat output.contree

