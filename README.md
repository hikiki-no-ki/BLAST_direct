--------------------------------------------------------
Project: pocket-BLAST: automatically execution of BLAST 
Date: 2019/12/28                                        
Author: Yusuke Hiki                                     
--------------------------------------------------------

## OVERVIEW
This project contains the programs to execute easily blast+ at CUI from input data including query sequences,
reference sequences, target gene names, setting file, and output directory path.
First, the database is made from reference sequences as pretreatment.
Second, target genes are extracted from query sequences and make the file Sequence_FocusedGene.fasta.
Finally, blastn or blastp is executed with the parameters written in ./setting.txt or default.

## DEPENDENCY
  * zsh >= 5.3
  * blast+ >=2.7.1 (ftp://ftp.ncbi.nih.gov/blast/executables/blast+/)
  * R >=3.4.2 (https://cran.r-project.org/index.html)

## EXECUTION
< Preparation >
```zsh
% git clone https://github.com/hikiki-no-ki/pocketBLAST.git
% cd ./pocketBLAST
% CURRENTDIR=`pwd`
% alias pBLAST='${CURRENTDIR}/pBLAST'
```

< Easy Usage >
 USAGE: pBLAST --mode ['blastn' or 'blastp']
               --query [query file path]
               --ref [reference file path]
               --setting [setting file]
               --outdir [output directory path]
               --sbh [query prefix] [reference prefix]
               --debug [0 or 1]
               --help

< Options >
   *        --mode(MUST): blastn or blastp.
   *       --query(MUST): query file path in fasta format.
   *         --ref(MUST): reference file path in fasta format.
   *      --outdir(MUST): output directory path to put BLAST result.
   * --setting(OPTIONAL): setting file in original format (template is ${pBLASTHOME}/setting.txt).
                          (The detail of options: https://www.ncbi.nlm.nih.gov/books/NBK279684/)
   *     --sbh(OPTIONAL): query and reference prefixes of Single-directional Best Hit table.
                          To make sbh available, output format must be 6 in setting file.
   *   --debug(OPTIONAL): debug mode not to remove file with writen execution command.
   *              --help: open this page

< Testcase >
```zsh
% cd ${pBLASTDIR}
% ./pBLAST --mode blastn --query ./testcase/test_query.fasta --ref ./testcase/test_reference.fasta --outdir ./testcase
```
and check the results in ./testcase .

## HAVE FUN !!
