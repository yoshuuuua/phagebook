# PhageBook


While bacteriophages are extremely abundant surprisingly little is known about them. PhageBook is a tool used to analyze and aid in the classification of bacteriophages.

## Getting Started
* Clone the PhageBook repository `git clone https://github.com/jblack332017/phagebook`
* Install pip using the following instructions https://pip.pypa.io/en/stable/installing/
* Install PhageBook, run `sudo pip install --editable .` in the phagebook directory
* Ensure PhageBook is installed by running `phagebook --help`

## Usage
Phagebook accepts a file containing a single bacteriophage capsid protein amino acid sequence in fasta format. 
Just like the following phiKZ.fasta:

```
>phiKZ MCP
MSVHALRELFKHKGEKNYEVFSMEDFIGRLESEIGLNDSVVSQG
RSLISSISHENFGTVQATDIQDAAAIYNKMQMLVNDYGFERVSSSDPQVRAREERVRE
NQITAATMAAIACADETKYIRALRGITKAKASNEDHVKVVQHQFNGPAGGIQVFENGV
GLENYNEKSQRDFRVVTIGYNLAASRQDEFAERIYPTTVINPIEGGVVQVLPYIAVMK
DVYHEVSGVKMDNEEVNMVEAYRDPSILDDESIALIPALDPAGSNADFFVDPALVPPY
TIKNEQNLTITTAPLKANVRLDLMGNSNANLLIQRGMLEVSDTIDPAGRLKNLFVLLG
GKVVKFKVDRLPRAVFQPDLVGDTRNAVIRFDSDDLVVSGDTTFIDGSADGVINDLKT
AKLSLRLSVGFGGTISLSKGDSKFGATDTYVDKVLNEDGQVMDNADPAVKAILDQLTD
LAVIGFELDTRFTNTNRRQRGHLLQTRALQFRHPIPMHAPVTLPMDTMTDEGPGEVVK
ALTVNTNIRNSNNAVKRMLNYLAQLREVVHNGYNRPKFGIIEGALSAVMRPTYRYKEL
DLEKVIDTIKSKDRWDDVCAAILNCVKAELFPAHRDSNIEAAFRVISGNQDETPMYLF
CSDKEIANYLMTKGDDRTLGAYLKYDIVSTNNQLFDGKLVVIPTRAVQQENDILSWGQ
FFYVSTVIADLPITRGGHQVTREIAAIPFNLHVNNIPFALEFKITGFQKVMGETQFNG
KLADLKP
```

PhageBook will then use blastp and the NCBI Entrata database to compile a a list of similar proteins and their corresponding Bacteriophage genomes. 

PhageBook will run the resulting proteins through the multiple sequence alignment tool ClustalW and output the resulting alignment file `proteins.aln` 

PhageBook will also generate a dotplot `plot.png` using Gepard

![alt text](https://github.com/jblack332017/phagebook/blob/master/Flow.png)

## Commands
The basic PhageBook command is structured `phagebook run <email> <path to protein fasta file>`

## Arguments
Arguments are required.
* `email` This is the email that will be reported to NCBI as part of PhageBook's queries
* `protein fasta format` This is the input protein that will be evaluated

## Options 
* `--maxevalue` Default: .15 - The maximum E value accepted during blastp
* `--alignformat` Default: clustal - The output of the alignment
* `--blastp/--no-blastp` Default: blast - Determines if blast will be run

A full command may look like the following:

```
$ phagebook --maxvalue 1.4 --no-blastp phagebook@example.com phikz.fasta
```

## Results

The `phagebook-results` file will be generated in directory that you call PhageBook from:
```
- phagebook-results
  -- sequenceIds.txt
  -- proteins.fasta
  -- genomeIds.txt
  -- proteins 
    --- ... all protein fasta files
  -- genomes 
    --- full.fasta
  -- proteins.aln
  -- proteins.dnd
  -- plot.png
```
* `proteins.aln` is an alignment file that can be read by clustalx
* `proteins.dnd` is a dendrogram of the protein alignment
* `plot.png` is the dot plot generated by Gepard

## Development 

PhageBook is an open-source project that current supports Mac OS, Linux, and Windows. You are free to alter and use PhageBook. Please contribute and add new functionality and improvements.



