# PatentSeq

# Background & Description

An easy-to-use script that converts **image-based protein sequences**
in patents to 3-letter coded or 1-letter coded **fasta** format.

# Dependencies

Install the following modules before running the script:
1. Pillow
2. Pytesseract
3. Biopython

# Increase Accuracy of Tesseract

## Train using your font
To increase accuracy of tesseract, try training it using your font file. Follow these simple steps to perform basic training:

1. Go to [trainyourtesseract](http://trainyourtesseract.com/) website, submit font file in OTF or TFF
2. Once you receive a `traineddata` file, drag it to the `tessdata` folder.

  An example of `traineddata` for "courier" font is provided here
  
3. To verify that you placed the `traineddata` in the right place, in Terminal, type:
```
tesseract   --list-langs
```
   You should be able to see your new file there.

4. In python script, invoke the new font with:
```python
pyt.image_to_string(img, lang="font") #single font
pyt.image_to_string(img, lang="font1+font2") #mulitple fonts
```

## Adjust Image-Processing Parameters
1. apply thresholds
2. adjust image size


# Examples of Usage

Example sequence can be found in the images folder. For details see Jupyter Notebook

*Source:*
- *Example 1: Patent US20170114146A1, Seq #29*
- *Example 2: Patent US20190183931A1, Seq #21*

## Image Preparation
Take a snapshot of the sequence image. **Be sure to LEAVE OUT the headers**. Below is an exmple of such image (available in images folder):

![](https://github.com/xinyu-dev/PatentSeq/blob/master/images/Example_Seq1.png)

## Simple Invokations

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

Example output: 
```
***************************************************************
*            Result (double check to verify)                  *
***************************************************************
>Seq shown in string 
Asp Ile Gln Leu Thr Gln Ser Pro Ser Thr Leu Ser Ala Ser Val Gly
1               5                   10                  15
Asp Arg Val Thr Ile Thr Cys Arg Ala Ser Glu Ser Leu Asp Asn Tyr
20                 25                 30
Gly Ile Arg Phe Leu Thr Trp Phe Gln Gln Lys Pro Gly Lys Ala Pro
35                 40                 45
Lys Leu Leu Met Tyr Ala Ala Ser Asn Gln Gly Ser Gly Val Pro Ser
50                 55                 60
Arg Phe Ser Gly Ser Gly Ser Gly Thr Glu Phe Thr Leu Thr Ile Ser
65                 70                 75                 80
Ser Leu Gln Pro Asp Asp Phe Ala Thr Tyr Tyr Cys Gln Gln Thr Lys
85                  90                  95
Glu Val Pro Trp Ser Phe Gly Gln Gly Thr Lys Val Glu Val Lys
100                 105                 110

>Seq in 1-letter code
DIQLTQSPSTLSASVGDRVTITCRASESLDNYGIRFLTWFQQKPGKAPKLLMYAASNQGSGVPSRFSGSGSGTEFTLTISSLQPDDFATYYCQQTKEVPWSFGQGTKVEVK

>Seq in 3-letter code
AspIleGlnLeuThrGlnSerProSerThrLeuSerAlaSerValGlyAspArgValThrIleThrCysArgAlaSerGluSerLeuAspAsnTyrGlyIleArgPheLeuThrTrpPheGlnGlnLysProGlyLysAlaProLysLeuLeuMetTyrAlaAlaSerAsnGlnGlySerGlyValProSerArgPheSerGlySerGlySerGlyThrGluPheThrLeuThrIleSerSerLeuGlnProAspAspPheAlaThrTyrTyrCysGlnGlnThrLysGluValProTrpSerPheGlyGlnGlyThrLysValGluValLys

```
