# Installation

## 1. Install anaconda python

help link: <https://www.anaconda.com/products/individual#windows> \
follow link and select the Anaconda3 for windows x86_64.exe \
After finishing the installation, add anaconda python path to 'C:\Anaconda3\Scripts'

## 2. Make virtual environment

write the command below \
  
Install new environment \
(1) conda create -n <Virtual_environment_name> python=<python_version_you_want> \
ex) conda create -n Deep_ML python=3.7
  
Activate new environment \
(2) conda activate Deep_ML
  
Install Keras into new environment \
(3) conda install keras \
(4) conda install tensorflow
  
Install jupyter \
(4) conda install ipykernel \
(5) python -m ipykernel install --user keras-gpu \
(6) conda install jupyter
  
if problem happen \

1) OpenSSL problem -> check this link (<https://stackoverflow.com/questions/55185945/any-conda-or-pip-operation-give-ssl-error-in-windows-10>) \

- find the conda installation path \
- find the files (libcrypto-1_1-x64.* & libssl-1_1-x64.*) in the CONDA_PATH\library\bin \
- move the files to CONDA_PATH/DLLs \
  
2) warning happen when import keras in python ('1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) /'(1,)type'.np_resource) \

- conda install numpy<1.17 <https://laondev12.tistory.com/13> \
  
*Anaconda command

- (check installation) conda --v \
- (check virtual environment list) conda env list

## 3. Connect with VS Code

1. Create new repository at Github
2. play the VS Code and click the source control button
3. Click 'initialize repository' button
4. Click '+' button which is next to file (changes to staging level)
5. Write comment and click commit button
6. Play terminal at VS Code
7. Type `git remote add origin [ 복사한 저장소 주소 ]`
8. Type `git pull origin main --allow-unrelated-histories`
9. Type `git push -u origin master` (push to remote repo)
10. Check the state at Github and click `Compare & pull request` button
