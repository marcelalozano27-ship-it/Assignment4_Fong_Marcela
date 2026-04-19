
### AI Usage Log - Assignment 4

### Marcela Lozano



#### Making the ipynb file output visible in GitHub

* **What task were you trying to do?**  
I was trying to make my ipynb file visible in GitHub because of widget issues in 
* **What prompt did you use?**  
I shared a screenshot of the GitHub error in Chat and asked why I was getting the error. 
* **What did AI suggest?**  
AI explained that the error happens because Colab uses some different widgets than GitHub. It suggested that I edit the JSON file to remove the part of the code with the widgets. I asked if there were any other options and it said that any progress bars would create the error when viewing in Github.
* **What did you modify?**  
I reran the top few cells in colab before putting the file on GitHub because that removed the progress tracker from the file output.
* **Why did you modify it?**  
I modified it because I wanted my output to be visible in GitHub.
* **What did you learn?**  
I learned that the progress trackers are not supported in GitHub and I just have to make sure that the output seen in Colab is supported by the viewing option in GitHub.
* **Any AI errors found?**  
The explanation given was correct but the solution given by AI was not that intuitive and I had to iterate with AI to get a simpler solution without having to edit the JSON file.
\---

### Exporting Annotation Samples from Label Studio

* **What task were you trying to do?**  
I needed to export only a subset of the annotated documents to train our model.
* **What prompt did you use?**  
"How can I export just a subset from Label Studio"
* **What did AI suggest?**  
AI explained I have to create a snaphot in Label Studio
* **What did you modify?**  
I used the filters on Label Studio, selected the data and created a snapshot. I made sure to set the export as `Default` so that I can export only the data I want.
* **Why did you modify it?**  
I modified it because I wanted to only output part of the data in Label Studio.
* **What did you learn?**  
I learned that creating snapshots in Label Studio is the best way to select subsets of the data.
* **Any AI errors found?**  
No Errors
\---
### Determining the Order of modeling

* **What task were you trying to do?**  
I was trying to make sure my code was in the most intuitive order.
* **What prompt did you use?**  
I uploaded the headings I used and the order I used them in within the notebook and asked if that order was correct.
* **What did AI suggest?**  
AI suggested I move around some of the cells to keep the pretrained model more organized.
* **What did you modify?**  
I moved the functions used for our custom spacy models to later in the notebook instead of cluttering the notebook and not keeping a clear notebook order.
* **Why did you modify it?**  
I modified it because I wanted my output to be visible in GitHub.
* **What did you learn?**  
I learned that the progress trackers are not supported in GitHub and I just have to make sure that the output seen in Colab is supported by the viewing option in GitHub.
* **Any AI errors found?**  
The explanation given was correct but the solution given by AI was not that intuitive and I had to iterate with AI to get a simpler solution without having to edit the JSON file.
\---
