
# What is a environment ?

A environment is a collection of tools/packages that will be used to perform some task.

When we talk about data science environment, we are talking about all the packages (pandas, numpy, matplotlib etc) and data (csv files, photos, music, videos etc) used in data science project.

There are many tools like Anaconda, Mini-Conda and Conda which help to set up the environment.

Anaconda already contains a lot of python packages that will be used in data science project.

Mini-Conda contains less python packages(compared to Anaconda) that will be used in data science project.

Conda is used to manage additional python packages in the environment.

So, instead of having all the packages and data in different location, we are isolating everything we need in a single folder. We can then just share this folder with anyone we like and they will have the same environment as ours.

# Miniconda

When we install miniconda, it comes with its default environment called base. This environment is installed in the condas installation directory i.e. ~/miniconda3.

Inorder to create a new environment, use command

conda create --prefix <environment location> <package 1> <package 2> <package 3>

To activate the new environment

conda activate <environment location>

To view all the environments

conda env list

To install a new package

conda install <package name>

To deactivate a conda environment

conda deactivate

To export a yml file containing information regarding our environment, use

conda env export --prefix <environment location> > <name of yaml file to be created>

To create a environment from this yml file,

conda env create --file <name of yml file to use> --name <environment name to be created>

conda env create --file <name of yml file to use> -p <location of environment name to be created>
