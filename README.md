# Evaluation and comparison of the RASP system and the Stanford unlexicalized PCFG parser
This project has been carried on as part of the final assignment of the L95 module. It aims at studying two parsing models: the RASP system (Briscoe et al., 2006) and the unlexicalized PCFG parser from the Stanford NLP tools. 

It is composed of multiple elements:
- a PDF report that describes all the work done, presents results and offers analyses about models and results
- a directory *data* that gathers two files with the sentences studied in this work
- a directory *parsers_output* that gathers parsers outputs for the previous sentences
- a directory *gold_standards* that gathers gold standards for the previous sentences in the Grammatical Relation format and the CoNLL format
- an XML file *eval.xml*, useful for the MaltEval evaluation system


## RASP system
To run the RASP system, you first need to download the RASP software and place the corresponding directory in the main directory of the project. Then, you can parse sentences with the RASP system thanks to the following command line:  

`RASP/scripts/rasp.sh -m < data/handout_sentences.txt > parsers_outputs/rasp_handout.txt`

It is possible to change the output format with different parser options. Here are some examples:
- `-p'-og'`: grammatical relations (default output format)
- `-p'-ow'`: weighted grammatical relations
- `-p'-nk'`: outputs at most k parses for each sentence


## Stanford unlexicalized PCFG parser
Once again, to run the unlexicalized PCFG parser from the Stanford NLP tools, you need to download the Stanford tool and place the corresponding directory in the main directory of the project. Then, you can parse sentences with the following command line:  

`Stanford_parser/lexparser.sh data/handout_sentences.txt`

Parsed sentences are printed directly in the console.

It is possible to change the output format by changing the `outputFormat` option in the *lexparser.sh* file. In order to obtain CoNLL dependencies, I set the output format option to `conll2007`. Other output formats are available, such as `penn` or `typedDependencies`.

 

## MaltEval tool
The MaltEval tool is an efficient tool to compare files in the CoNLL format, and therefore evaluate the performance of a parser by comparison with gold standards. To use this tool, you need to download the MaltEval software and place the corresponding directory in the main directory of the project. Then, you can compare two CoNLL files with the following command line:  

`java -jar MaltEval/lib/MaltEval.jar -e eval.xml -s parsers_outputs/stanford_output.conll -g gold_standards/gold_standards.conll`

Statistics about the parser's performance are directly displayed in the console.



