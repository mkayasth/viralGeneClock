<h2> Introduction </h2>
Using ViralGeneClock, the users can deposit the whole genome sequence (WGS) of different strains of a virus. The tool then examines the evolutionary relationship of the strains, and also estimates the relative mutation rates of the genes across these strains. It leverages Prokka for viral genome annotation, Muscle for multiple sequence alignment of each gene for different strains and the Neighbor Joining Algorithm for determining genetic distances and branch lengths. ViralGeneClock utilizes the genetic distance and branch length data to then provide relative mutation rates for each annotated gene. This is primarily a Linux tool developed through the Linux subsystem.<br> <br>

The final output .zip folder <b>(outputs.zip)</b>is emailed to the provided address. Outputs from the full genome analysis is saved in the folder <b>fullSequence-output</b>. Results from gene-specific analyses are saved in the folder <b>geneAnalysis-output</b>, and the output for relative mutation rates is saved in the folder <b>avg_mutation_rate_final</b>.

<h2> Installations </h2>
<h3>1) Prokka:</h3> For detailed Prokka installation instructions for your OS, visit this site: https://github.com/tseemann/prokka <br> <br>
 
For brew users in Linux: <br>
minced does not properly install via brew; but minced is not required for viral annotation. After Brew installs Prokka, uninstall minced, and start working!

 ```shell
brew install brewsci/bio/prokka
brew uninstall --ignore-dependencies minced
```

For Ubuntu users with sudo access, you can also follow these steps:
```shell
sudo apt-get install libdatetime-perl libxml-simple-perl libdigest-md5-perl git default-jre bioperl
sudo cpan Bio::Perl
git clone https://github.com/tseemann/prokka.git $HOME/prokka
$HOME/prokka/bin/prokka --setupdb
```
<h4> Add Prokka to your PATH. </h4> <br>

<h3>2) Muscle:</h3> For detailed Muscle installation instructions for your OS, visit this site: https://github.com/rcedgar/muscle/releases/tag/5.1.0  <br>
<h4> Add Muscle to your PATH. </h4> <br>

<h3>3) Python3:</h3>

If you have pip installed for your Python3, follow these steps:

```shell
python3.11 -m pip install biopython
python3.11 -m pip install matplotlib
python3.11 -m pip install flask
python3.11 -m pip install flask-mail
```

<h3>Note: </h3>This tool executes scripts using the 'python3' command, so ensure Python 3 is installed on your system. Additionally, all required packages mentioned above must be installed for the Python3 environment that is invoked when you run 'python3' from the command line. <br> <br>

You may need to set xcb as the Qt platform plugin for obtaining the matplotlib produced tree.jpg. Follow these steps:

```shell
sudo apt-get install libxcb-xinerama0
export QT_QPA_PLATFORM_PLUGIN_PATH = /path/to/qt/plugins/platforms
export QT_QPA_PLATFORM = xcb

```

<h2> Usage </h2>

After completing necessary installations, run the web app with app.py :) <br>

 ```shell
python3 app.py
```

<br> 
Alternatively, you can use the command line interface with main.py (app.py calls main.py using the subprocess library). <br>

 ```shell
python3 main.py <input_fasta_file> <reference strain>
```

The <input_fasta_file> comprises the complete set of whole genome sequences (WGS) for the strains you intend to analyze. Each strain's FASTA header should be the name of the strain.

