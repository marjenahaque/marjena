[Home page](./)&nbsp;&nbsp;&nbsp;[Education](./education.md)&nbsp;&nbsp;&nbsp;[Work](./Work.md)&nbsp;&nbsp;&nbsp;[My Blog](./My_Blog.md) 

# How to rename multiple files by removing common prefix of file name
Suppose you have several files with common prefix in file name. You want to rename all file by keeping only last part of the name. 
For that we only need `os` library to interact with operating system to list all files in directory.
```python
import os
```
**Specify the directory containing your files**

```python
directory_path = r'C:\Users\path\to\your\file'
```
**These are my csv files**

![pic1](https://github.com/marjenahaque/marjena/blob/main/images/Common_prefix.png?raw=true)

**Specify the common prefix to be removed**
```python
common_prefix = 'cesm2_quantile_corrected_cesm2_pcp_'
```
**List all files in the directory**
```python
files = os.listdir(directory_path)
```
**Iterate through each file. Check if the file is an Excel file (you can adjust this condition based on your file naming pattern).
Extract the last part of the file name (excluding the common prefix). For that we will use `:`as it is for slicing.**
```python
for file in files:
    if file.endswith('.csv'):
        new_name = file[len(common_prefix):]
        # Create the full path for the old and new file names
        old_path = os.path.join(directory_path, file)
        new_path = os.path.join(directory_path, new_name)
        # Rename the file (replace the existing file)
        os.rename(old_path, new_path)
print("File names have been updated successfully.")
```
**Here is the output**

![pic2](https://github.com/marjenahaque/marjena/blob/main/images/without_prefix.png?raw=true)
