# SC_Template
**Objective**: 
The primary purpose of this Short Courses (SC) repository, **SC-Partner-Cx**, is to enable the instructor, their team and the DLAI team to collaborate on the content before filming, ultimately using the final notebooks here as an instructor guide for filming.

The final filmed notebooks, along with all dependencies and files (utils, helper, and datasets), will be copied to another repository named **SC-Partner-Cx-Platform**. This will be referred to as the platform final repo and will be maintained with all the notebook content available on the platform.

**Platform directory structure**:

The platform maintains a directory structure where each lesson is self-contained.
It contains only the student material. Each lesson may be in a separate docker container (no sharing data between lessons).

Here is an example:
```
├── helper.py
├── ro_shared_data
│   └── some_data.csv
├── L1
│   └── Lesson1.ipynb
│   └── ro_shared_data(symbolic link)
│   └── helper.py(symbolic link)
├── L2
│   ├── Lesson2.ipynb
|   ├── data.jsonl
│   └── helper.py(symbolic link)
├── README.md
├── .env (stores keys, not in git)


```
shared data is 'ro' or read-only because data written in one lab is not visible in later labs as they may be in separate docker images.
Labs may also be incorrectly run or not run at all and later labs should still behave well.

Typicaly a course has 4-6 lessons. You will have to create those directories

**Template Content**:

As a course creator, there are some useful guides in this template:

* When we film, to make the code readable, we zoom into the code. Concretely, in Chrome, we set zoom to 150%. Along with the 8x9 screen format, this leaves a fairly narrow code area. Specifically, 72 characters across in the default Jupyter font. It's easier to write the code in that format than to adjust it later! This is described along with some long-line techniques in L1.
* The repository has a directory structure where each lesson is in a separate folder. This makes it simple to dockerize each lesson independently in the future. Note that if there is a shared helper file or shared data files or data directory, they should go on the top level with symbolic links to them in the lesson directories.[CPMs, when the directories are 'scp'ed to the platform, the symbolic links will be replaced by copies of the files leaving each directory self contained as desired.] Symbolic links in linux are *alias* in mac parlance. Sometimes they are referred to as shortcuts. The links are setup in L1 and L2. To add additional links to L3 for example:
    * cd into L3
    * ln -s ../helper.py 
* The first lab also shows how api keys are managed. We store them in a .env file which is then pulled into environmental variables with a python package python-dotenv. The .env file is ignored by git via the .gitignore file (also part of the template) so that personal keys are not shared to git
Here is an example of the format of the .env file:  
OPENAI_API_KEY=sk-ThisCourseWillPutAFakeKeysInTheStudentDir.envFileIfNeeded  
SOMEOTHER_API_KEY=sk-ThisCourseWillPutAFakeKeysInTheStudentDir.envFileIfNeededtoo


**Note**:
The .gitignore ignores files typically ignored in Jupyter notebooks
The .gitattribute is used to treat Jupyter files as binary to prevent merging.

**Sandboxes used during testing and filming**:



