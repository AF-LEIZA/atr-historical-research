# Strategies for optimising layout recognition

## Digitisation as part of the transcription

As Koen Hufkens explained in his talk at IEG Mainz on 6 February 2025, digitisation is already part of the transcription and those who are making their own photos or scans of sources should pay attention to the following aspects:

- experiment with different (paper) backgrounds, especially when paper is slightly transparent, gray or black backgrounds may work better than white backgrounds
- consider preparing a grid for precise document alignment
- consider creating a frame or passepartout for documents of different sizes

Koen has also collected [best data practices](http://cobecore.org/research/data-best-practices/) from his COBECORE climate data project, which may be useful for researchers from different disciplines.

## Basic layout recognition with Spacy Layout

The [```spacy-layout```](https://spacy.io/universe/project/spacy-layout) package can help with more basic layout recognition (for PDF documents). It "outputs spaCy’s familiar ```Doc``` objects that let you access labelled text spans like sections, headings, or footnotes."

## Layout recognition with computer vision

When working with tabular data and/or data that were collected in standardised forms (e.g. scientific tables, telegrams, or government reports), you may want to consider using computer vision to identify (handwritten) text within the documents and improve text segmentation. One powerful library for template matching is [OpenCV](https://docs.opencv.org/4.x/d4/dc6/tutorial_py_template_matching.html). In your workflow, you need to list all the documents you want to process and then perform a batch-template matching (e.g. based on a clean template defined with the [GIMP](https://www.gimp.org/) image manipulation software). You can define bespoke text areas in your template and save them to JSON files that can then clearly align found text with metadata (such as archival numbers, dates, names, or places). Then you can use a Python script (set up to be run in a Docker image for better dependency management and security). The actual OCR model that Koen Hufkens used for his transcription of climate data from the Belgian Congo was the French-language model for Tesseract. To learn more about the Tesseract Page Segmentation Modes (PSMs), read [Tesseract Page Segmentation Modes (PSMs) Explained: How to Improve Your OCR Accuracy](https://pyimagesearch.com/2021/11/15/tesseract-page-segmentation-modes-psms-explained-how-to-improve-your-ocr-accuracy/) by Adrian Rosebrock. Koen has documented his process for working with handwritten tabular data originally collected in (pre-printed) form in the [BlueGreen Labs GitHub](https://github.com/bluegreen-labs) repository under **weaHTR data recovery workflows**. Koen Hufkens is active on GitHub as [khufkens](https://github.com/khufkens?tab=repositories).

## Making use of (recurring) structural features

In layout recognition, it also often helps to think about your data in a very structural, physical sense first. Consider where text on your pages clusters, where white space / negative space defines column formats, and where certain data come up in a fixed order. This can help you improve layout recognition based on truly human perceptions of the data before letting a machine approach it from an algorithmic perspective. Inspiration may come from John Scancella's blog post [Better OCR for Newspapers](https://medium.com/@blacksmithforlife/better-ocr-for-newspapers-c7c1e2788b7a). 

## Simple batch-processing of images

If you want to perform more simple image cropping and rotating to improve layout recognition, you can consider using the [batch mode in GIMP](https://www.gimp.org/tutorials/Basic_Batch/) if your images are similar. There are also options to batch-process images via the computer command line, e.g. for splitting columns or separating pages.
