Hadjixenofontos Lab 
Coding Standards

## Development 

TODO
Develop interactively, but then copy everything into a script

## Project organization

Any project should follow the following directory structure:
/Users/username/project_name
	scripts/
		readme.txt
		MM-DD-YYYY-analysis-keyword/
	plots/
		readme.txt
		MM-DD-YYYY-analysis-keyword/
	original_data/
		readme.txt     
	manipulated_data/
		readme.txt
		MM-DD-YYYY-analysis-keyword/
	results/
		readme.txt
		MM-DD-YYYY-analysis-keyword/
	readme.txt

The /Users/username/project_name path will differ depending on your operating system (OS). Whichever your OS, the project_name directory should live in your home directory. 

Everytime you generate output, plots, or a version of manipulated data, they should be saved in the corresponding date-matched directory. 
If the files are too big, first confirm that they can be re-generated if neeeded, with the data and scripts that you have, and then delete them once they are no longer needed by subsequent steps. 

#### The MM-DD-YYYY-analysis-keywords directories

It is up to you to decide when to start a new MM-DD-YYYY-analysis-keyword folder. Please take into account whether you expect to switch gears, for example your first folder is likely going to be MM-DD-YYYY-quality-control. When the QC phase quietens down, you'll likely make a new directory MM-DD-YYYY-exploratory-analyses. 

Please make a new folder for each method that you apply to the data, for example MM-DD-YYYY-random-forests or MM-DD-YYYY-kmeans-clustering. 

If any of these directories will include a single file, e.g. because you are using a Jupyter notebook, then don't make them into directories, but instead follow this naming convention for your notebook files. 

#### What should go in the readme.txt files

Every directory should have a readme.txt file. The purpose of these files is to orient you and anyone else who will look at your work to the contents of the directory. 

These should grow continuously as you build up your analysis. 
- readme.txt
TODO
- scripts/readme.txt
	- Should contain the steps that you went through in the analyses, including justifications for your decisions to e.g. use a specific method. Don't include details of your implementation decision-making here, those belong as comments inside the scripts themselves.  
- original_data/readme.txt
	- Should contain where you got the data, when it was downloaded to this location, and who was your source (if a person was involved). If you used an API to obtain the data, please provide version details and a link to the API documentation.  
- plots/readme.txt
TODO
- manipulated_data/readme.txt
TODO
- results/readme.txt
TODO

#### When to overwrite files

Figuring out when to overwrite files, vs when to keep a record of what was done by creating a new file and keeping an old copy intact, is a tricky decision to make. In general, if the new file you are creating has implications for the rest of the analysis and interpretation of the results, create a new file. If the new file is simply an intermediate file in your development of a script, then overwrite the file. Of course, if the old file is likely to be helpful in you figuring out what works while you develop your scripts, then keep it until you have figured out that piece of the implementation and the old file is no longer needed. 

## Environment management 

Our goal is to minimize the probability that our future selves (or others who will inevitably re-run our analyses) cannot do so unambiguously. One reason why they may not be able to re-run our scripts is a difference in environments. There are multiple ways to share the setup of your environment. You can share an environment configuration file (often a YAML file) 

#### Shell environments
There is one occasion where it is not necessary to 

#### Python environment management

Creating isolated environments for your project is not only a good idea to avoid dependency issues when your list of projects grows, but also makes it easier for others to use your code, including others in our lab. All they'll have to do is recreate your environment by running a configuration file that you provide, and they'll be able to run your code without environment-related errors. 

Use conda as the environment manager. Download from https://conda.io/docs/user-guide/install/download

Create a new environment that is specific to this project. Include in it any packages that you anticipate you will need for the project. Some standard libraries to include are numpy, scipy, pandas, maplotlib, seaborn, and scikit-learn. Use this guide to help you create a new environment:
https://conda.io/docs/user-guide/getting-started

When sharing your environment.yml file with others, please export it by following this guide:
https://conda.io/docs/user-guide/tasks/manage-environments

## Reproducibility matters

In general, you want to create an analysis pipeline such that anyone coming in without any knowledge of the decisions you made along the way will be able to run your scripts in the correct order and reproduce your results, without any ambiguity about what you did at any stage of the process.

In order to do this follow these guidelines:

#### Graphical user interfaces (GUI)

Do not open data files or output files in a text editor and definitely do not ever open them in a spreadsheet program. This has the potential to introduce errors that may go unoticed, and to alter the hidden characters that are present in all files, causing them to behave differently than expected when using command line tools. 

If you'd like to take a look at the contents of a file you can use shell commands (head, less -S) or load the data into an R dataframe or a Python pandas dataframe and examine it using the relevant statements and expressions.

Any, absolutely ANY, manipulations you make to a file should be made programmatically, whether in shell, Python, R scripts or other scripts.   

The only exception to this are manifest files. For manifest files (i.e. those that document metadata about samples) this topic is a gray area, because you will likely not need to use those with command line tools. 

The bottom line is to keep your GUI and CLI files separate. If a file needs to be accessible to CLI tools, don't open it in a GUI.  

#### Local and remote git repositories
TODO


## Jupyter notebooks

In data analysis, it is useful to keep a lab notebook, which records your train of thought and intermediate results and other output as you develop your analysis pipeline. You can use Jupyter notebooks with shell, python or R code. (Shell notebooks are tricky on some operating systems ...)

Install, launch and learn how to use jupyter notebooks (global environment should be ok) using this guide http://jupyter.readthedocs.io/en/latest/running.html 

#### When to create a new notebook

Please create separate notebooks for each analysis stage, similar to the guidelines above about how you would create separate MM-DD-YYYY-analysis-keywords folders. 

If you use Jupyter notebooks in your project, you will have a set of development notebooks, where you record your notes, comments, code and output while you are working out what works (developing). Additionally, you will have report notebooks, which will tell a story. These will be a snapshot of where you are in your analysis, and as such will include only the code pieces that work to create the story that you want to tell through the report. It is unlikely that you will need to create multiple of these, and most likely that you will only need to create one, at the end of this project as a final report. 

#### Special considerations for plots

If you are using Jupyter notebooks, plots will save inside the notebook itself, which will live in the scripts/ directory. In this case, the plots/ directory should only contain plots that you make with software that you can't use inside a Jupyter notebook, or publication-related plots, or any plots which for any other reason can't live inside the notebook. 

#### Working on a cluster

If you have to work on a cluster, you probably won't have access to a GUI, and so nevermind Jupyter notebooks. Instead, keep very detailed and extensive comments inside your scripts. Please include comments on previous implementation approaches that you took and the reasons why they didn't work out. The plots will save outside of that file, but that's alright. 

## Develop interactively, run the final version from a script
TODO

## Avoid hardcoding
TODO

## Variable naming conventions
TODO

## Write your code modularly
TODO

## Further reading

Please read the following paper on best practices, and follow them as best as you can!

Noble, A Quick Guide to Organizing Computational Biology Projects, PLOS Computational Biology, 2009
http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424

Wilson et al., Good enough practices in scientific computing, PLOS Computational Biology, 2017
http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510

Wilson et al., Best Practices for Scientific Computing, PLOS Biology, 2014
http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745

