# PatentSeq

# Background & Description

An easy-to-use script that converts **image-based protein sequences**
in patents to 3-letter coded or 1-letter coded **fasta** format.

A large portion of sequences provided in pdf patents are embedded as images, or in an user-unfriendly format difficult for copying/paste. It generally requires much manual work to convert these seqs into fasta. With this script, you can simply take a snapshot of any protein sequences from patents, run it and get your sequence in 3-letter coded and 1-letter coded **fasta** format.

# Dependencies

Install the following modules before running the script:
1. Pillow
2. Pytesseract
3. Biopython

# Examples of Usage
Example sequence can be found in the images folder. For details see Jupyter Notebook. 

*Source: Patent US20170114146A1, Seq #29.*

## Simple Invokation
Take a snapshot of the sequence image. **Leave out the headers**. (see Example_Seq1.png in the images folder for an example of such image). Then invoke with: 

```python
result=PatentSeq("Example_Seq1.png")

#print results
print(">Seq shown in string ")
print(result[0])

print("\n>Seq in 1-letter code")
print(result[1])

print("\n>Seq in 3-letter code")
print(result[2])
```
