
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
AI explained I have to create a snaphot in Label Studio.
"Step-by-step
Open your project in Label Studio
Go to Tasks
Use filters at the top:
Filter by:
Annotated = Yes
Annotator = your name (if needed)
or Task IDs if your instructor assigned specific ones
Select the exact 10 shared documents
Click Export"

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
I modified it because I wanted the order of the workflow to be intuitive to the viewer.  
* **What did you learn?**  
I learned that in order to keep the best notebook structure I should define the functions only right before they will be used as this can make the order of the notebook more cohesive.
* **Any AI errors found?**  
I didn't completely agree with some of the order changes recommended so I used the AI recommendation as a guideline and adjusted as needed.
\---

### Improving Model Recognition of Entities

* **What task were you trying to do?**  
I was trying to understand why my model was performing so badly even after training it with annotations.
* **What prompt did you use?**  
"im working on a ner model and my metrics after training the model are still very low. the type of data i am analyzing twitter data and i want the handles to be recognized as a person but they do not have an @ sign"
* **What did AI suggest?**  
AI suggested that I add more examples of entities in our specific text and expand our annotation guidelines.
* **What did you modify?**  
We made sure to be more precise when setting ground truths and tried to focus on only using data that has meaningful entities.
* **Why did you modify it?**  
I modified the kinds of ground truths we used because I wanted the model to learn the actual entities in our specific Twitter text.
* **What did you learn?**  
I learned that the way to actually improve the model is by providing more data for the model to be trained on.
* **Any AI errors found?**  
The recommendations provided were useful and actually improved the model.
\---
### Are URL's typically labeled as LOC

* **What task were you trying to do?**  
I was trying to figure out whether typical NER labeling consideres a URL as a location.
* **What prompt did you use?**  
Are URL's typically considered a `LOC` entity in NER?
* **What did AI suggest?**  
"In NER labeling (especially Broad Twitter Corpus style: PER / ORG / LOC), a URL should usually not be labeled at all unless your instructions explicitly say otherwise."

* **What did you modify?**  
I made sure to not mark URL's as LOC entities. We also checked the data to see if it was worth adding an entity to capture URLs but ultimately decided that there were not sufficient examples in the dataset to need to include another entity.
* **Why did you modify it?**  
I wanted to make sure we were using appropriate labeling.
* **What did you learn?**  
I learned that it's important to be incredibly consistent in labeling in order for the model to learn appropriately.
* **Any AI errors found?**  
No errors
\---
