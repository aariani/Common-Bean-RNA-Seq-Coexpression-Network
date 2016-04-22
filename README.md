# Common Bean RNA-Seq Coexpression Network

###This repo contains Coexpression Network and Pearson Correlation Coefficients (PCC) based on expression analysis of 85 RNA-Seq datasets. 
The RNA-Seq data were downloaded from the [NCBI SRA archive] (http://www.ncbi.nlm.nih.gov/sra).

===========================================================================================================

In the folder `Pipelines` there are the scripts used for creating this dataset (Refer to the readme file inside the folder).

In the folder `Coexpression_Data` there are 2 files with the inferred Coexpression Network:

* Pvul_coexp_net.txt is a tab-delimited file with two column indicating a vertex between two edges (genes)
* Pvul_coexp_net_PCC.txt is a similar to Pvul_coexp_net.txt but contains a 3rd column showing the PCC.

Both the files used a PCC threshold of 0.8
These data are compatible with several programs for network visualization and analysis like [Cytoscape] (http://cytoscape.org/) and could be directly used for research studies

===========================================================================================================

The folder `Raw_coexpression` contains 18050 files named with common bean gene ID accordingly to [Phytozome platform] (www.phytozome.net). 

Each file is tab-delimited and contains 2 columns:

1. GeneID
2. PCC between the gene that named the file and the gene in column 1.

These data are intended for extracting common bean coexpression network using custom PCC threshold
The network could be inferred using the `inferNetwork` script in this folder.

===========================================================================================================

## Download this repo

For clone this folder to your computer first you need to install git.
Let us assume you want to clone this repo into a directory named `proj`, you will need to open the terminal and type:

    mkdir proj
    cd proj
    git clone https://github.com/aariani/Common_Bean_RNA-Seq_Coexpression_Network

   
===========================================================================================================

## Extract coexpression network

For extracting the coexpression netowork you will need the `inferNetwork` script. This is a simple Python script, so just make sure you have python installed on your computer (Python 2.7+). 
First you need to make the script executable, so from the command-line type:

    cd Common_Bean_RNA-Seq_Coexpression_Network
    chmod +x inferNetwork

Execute the script in the same folder where the `raw_coexpression` folder is (i.e. in this folder)
To see the command-line option type from the terminal:

    inferNetwork -h
        usage: inferNetwork [-h] [-i INPUTFOLDER] [--pcc] [-t MINPCC] [-o OUTPUTFILE]
        Program for exctracting coexpression networks based on Pearson Correlation
        Coefficient (PCC) data
        optional arguments:
            -h, --help          show this help message and exit
            -i INPUTFOLDER, --input INPUTFOLDER
                                The folder containing the Raw Coexpression data
                                (Default: raw_coexpression)
            --pcc               Do you want to export also the PCC value between genes?? (Default: False)
            -t MINPCC, --threshold MINPCC   
                                Minimum threshold for the PCC. Values < than this values will be discarded (Default: 0.8)
            -o OUTPUTFILE, --output OUTPUTFILE      
                                Name of output file (Default: CoexpressionNetwork.txt)


