# Machine-Learning-2015-Summer
Proj.py Official User Guide 2015

Downloading, Installation, and Running:
First, install this. This will install almost everything you need.
http://orange.biolab.si/download/files/orange-win-w-python-snapshot-hg-2015-07-06-py2.7.exe

This will install Python 2.7, numpy, scipy, and Orange for windows.

This package is recommended to those installing Orange for the first time. It includes all required libraries (Python, PythonWin, NumPy, PyQt, PyQwt ...), though it will not change any libraries you might already have.

Next, download and install this: https://www.python.org/ftp/python/2.7.10/python-2.7.10.msi

Create a new folder called “Machine-Learning”:
1. proj.py (Our main summer project code)
2. Orange_ML.py (Machine Learning for Cross-Validation and Leave-One-Out)
3. Orange_ML_two.py (Machine Learning for Test and Learn on Test Data [Train learning algorithms on all but one participant, and test them on that left-out participant])
4. saxpy.py (SAX)
5. arffgen.py (Diane’s Arff Generator)
6. conditions_(starter)001-(starter)00X.csv (The Excel files for conditions)
7. (starter)001-(starter)00X_All_Data.csv (The Excel files for the Oxy/Deoxy levels)
8.(Optional) ROI_(starter)001-ROI_(starter)00X.txt(ROI text files) OR ROI_file_(starter)000s.txt

For 8.,there are two lines of code, one supporting ROI_(starter) and one supporting ROI_...000s.txt, Just comment/uncomment out which line you are using/not using

You should have multiple files in one folder/directory per set of conditions: 5 Python code files, many Conditions files, many Participant Data files, and 1 ROI file.

Further instructions for parameters provided in proj.py. Only that file needs to be edited.
Simply run proj.py. It will do the rest. You can adjust the parameters as follows:

Once installed, open IDLE (Python GUI). If you have multiple, it usually is the lowest one. Make sure it says Python 2.7.10 at the top. Then go to File -> Proj.py, Run, Run Module.


Parameters:

word: # of words per SAX line.

letter: alphabet size per letter in SAX. Currently does in numbers for better machine learning accuracy (If the letter length = 3, for example, SAX representation will be numbers 1 through 3 per position).

starter: starting number for the experiment. If starter = 2, then the experiment is for 200X-20XX

p_start: starting participant for the experiment. If p_start = 1, participant is X001. If p_start = 2, participant is X002.

p_end: last participant for the experiment. If p_end = 5, last participant is X005.

zscore: Z-score - True/False Only. Will either z-score the data, or won’t.

roi: Region of Interest Analysis. True/False Only.

conditions: set this to what conditions you want. 12 = conditions 1 vs 2. 134 = conditions 1 vs 3 vs 4.

ext: file extension. Make sure this reflects the conditions. 12, make this look like ext = ‘1v2.csv’

num_k: Number of neighbors. Set this to whatever you’d like. The code automatically does 0 neighbors, num_k number of neighbors (your choice), 3 neighbors, and 5 neighbors. All can be seen in the .csv ML files.

n_num: How many features you’d like to use. Currently set to 100. Thus N = 100. Code currently does N/3, N/10, and N = 100. Therefore leave this at 100, but if you want to change it, this is how. If you change this to say, 200, you’ll want to go into both “Orange_ML.py” and “Orange_ML_two.py” and change where it says “N = 100” to “N = 200” instead.





What Our Code Actually Accomplishes:
Our code will take each participant + their conditions file, and:
Open the necessary .csv files
Split the .csv “All_Data” file into Oxy/Deoxy files
Create a Marks file (required for the .arff generator)
Make an .arff file and a .tab file (SAX) used in Machine-Learning
Concatenate data
Z-Score the data (if wanted)
ROI - Region of Analysis (if wanted)
Do 3 types of Machine Learning separated into two different .csv excel files per participant, and then to all the data that was concatenated into one “All_3000s_Data” file. The Machine Learning will tell you the accuracy and the AUC (area-under-the-curve).


Running Code Simultaneously:

If you would like to run “proj.py” simultaneously so that you can run multiple sets of conditions at once over the course of a week, here is how. The below example will show you how to run multiple sets of conditions at once: conditions 1 vs 2, conditions 3 vs 4, and conditions 2 vs 3 vs 4. The combinations are yours to choose.

With that “Machine-Learning” folder you created earlier, copy that and make additional copies. You should have identical folders but you’ll change the names of the folders. See the next step for names.
Name them by conditions--one folder could be “Machine-Learning 1v2”, another “Machine-Learning 3v4”, and then “Machine-Learning 2v3v4”. Again, this is your choice for what conditions you’d like to test out, but this is an example.
Modify the “proj.py” parameters in each of the folders. In the “Machine-Learning 1v2” folder, make sure to change the proj.py parameter “conditions” to ‘12’ and the “ext” parameter to ‘1v2.csv’. In the “Machine-Learning 3v4” folder, make sure to change the “conditions” to ‘34’ and the “ext” to ‘3v4.csv’. In the “Machine-Learning 2v3v4” folder, make sure to change the “conditions” to ‘234’ and the “ext” to ‘2v3v4.csv’.
The above steps will allow you to run multiple “proj.py” files simultaneously and get all the results in the correct folders so that you can leave multiple sets of code running on separate processors to maximize efficiency and not waste time. Instead of needing days/weeks to run one set of conditions, you can have all sets of conditions run simultaneously and get all the results you want in 1 week.
