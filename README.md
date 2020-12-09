# CardsLimitsMaker

## Installation

### extractBins
To run this code, the code in the `extractBins` folder must be compiled using the command:

```
make compile
```
Note that in order for the program to compile, ROOT and DELPHES must be installed in your system. Please see the `./extractBins/Makefile` file if you need to tweak the values for the delphes and exRootAnalysis folders. 

### Python 3

Additionally, python3 must be installed along with the libraries:

```
pandas
numpy
argparse
```

You can install them manually or in bulk with the `requirements.txt` file with the command `pip install -r requirements.txt`. A virtual environment with `pip` or `conda` is recommended.



## Usage

To run the program, type the following command in your terminal replacing `<your config.json>` with the path to your configuration file.

```
    python3 main.py -config <your config.json> 

```

### Configuration file

In order to run the program, you need to congfigure the configuration file in `JSON` format. 
The input files needed to generate the cards need to have the format:
```
folder with the name of the channel
	signal 1 root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	signal 2 root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	.
	.
	.
	signal n root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	background 1 root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	background 2 root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	.
	.
	.
	background n root file
		histogram 1
		histogram 2
		.
		.
		.
		histogram n
	
```
Configuration file explained:

```
{
     "channelPath" : <path to input data>,
     "sysUncertFile": <path to the systematic uncertanties file>,
     "studyType" : {
		 			"type": <exp or pheno>, 
	 				"data": <only for exp, path to the root file with observational data>
					 },
     "outputPath" : <output folder path>,
         "signals":[
				<name of signal 1 without .root extension>,
				<name of signal 2 without .root extension>,
				.
				.
				.
     ],
         "backgrounds":[
				<name of background 1 without .root extension>,
				<name of background 2 without .root extension>,
				<name of background 3 without .root extension>,
				.
				.
				.
     ],
     "histograms": [
		{
			"name" : <name of histogram 1>, 
			"binEdges" : <list of floats with histogram bins, for example: [0.0,40.0,60.0,80.0,100.0,120.0,140.0,160.0,300.0]>
		},
		{
			"name" : <name of histogram 2>, 
			"binEdges" : <list of floats with histogram bins for histogram 2>
		}
     ]
 }

```

With the configuration file defined, all that is left is to run the program.

Happy coding! 

