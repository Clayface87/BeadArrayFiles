# IlluminaBeadArrayFiles
Library to parse file formats related to Illumina bead arrays. GTC files are produced by the AutoConvert and AutoCall softwares and contain genotyping (and other) information encoded in a binary format. The IlluminaBeadArrayFiles library provides a parser to extract information from these binary files. 

## Build instructions
The IlluminaBeadArrayFiles repository supports building a package with the python distutils module (https://docs.python.org/2/distutils/setupscript.html). To build a source distribution, run the included setup.py script supplying the "sdist" command

>python setup.py sdist

## Installation instructions
After unpacking the installation package, run the setup.py script supplying the "install" command

>python setup.py install

If the user prefers not to use the python distutils framework, it is also possible to copy the IlluminaBeadArrayFiles.py source file into a location referenced by the PYTHONPATH environment variable.

## Example usage

> from IlluminaBeadArrayFiles import GenotypeCalls, BeadPoolManifest, code2genotype  
> import sys  
> gtc_file = "path_to_genotypes.gtc"  
> manifest_file = "path_to_manifest.bpm"  
> names = BeadPoolManifest( manifest_file ).names  
> genotypes = GenotypeCalls( gtc_file ).get_genotypes()     
> for (locus, genotype) in zip( names, genotypes ):  
> &nbsp;&nbsp;sys.stdout.write( locus + "," + code2genotype[genotype] + "\n" )

## GTC File Format
The specification for the GTC file format is provided in docs/GTC_File_Format_v5.pdf

## Description of classes and objects in exposed in package
For further details on specific class methods, please consult the built-in docstring documentation

### code2genotype
Dictionary mapping from genotype byte code (see GTC file format specification) to a string representing the genotype (e.g., "AA")

### NC, AA, AB, and BB
Constants representing byte values for associated genotypes

### GenotypeCalls
Class to parse GTC files as produced by Illumina AutoConvert and AutoCall software.

### NormalizationTransform
Class to encapsulate a normalization transform for conversion of raw intensity data to normalized intensity data

### ScannerData
Class to encapsulate the meta-data collected in the GTC file for a scanner instrument

### BeadPoolManifest
Class for parsing a binary (BPM) manifest file. This class can be used to recover the in-order list of loci names in a given manifest, which is necessary to associate the genotype information present in the GTC file to a specific locus name. 


## Compatibility
This library is compatible with Python 2.7 and was tested with Python 2.7.11

## License

>Copyright (c) 2016, Illumina
> All rights reserved.
>
> Redistribution and use in source and binary forms, with or without
> modification, are permitted provided that the following conditions are met:
>
>1. Redistributions of source code must retain the above copyright notice, this
>list of conditions and the following disclaimer.
>2. Redistributions in binary form must reproduce the above copyright notice,
>this list of conditions and the following disclaimer in the documentation
>and/or other materials provided with the distribution.
>
>THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
>ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
>WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
>DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
>ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
>(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
>LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
>ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
>(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
>SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
>
>The views and conclusions contained in the software and documentation are those
>of the authors and should not be interpreted as representing official policies,
>either expressed or implied, of the FreeBSD Project.




