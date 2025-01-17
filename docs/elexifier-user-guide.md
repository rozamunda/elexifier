# Elexifier User Guide

Welcome to the *Elexifier User Guide*. Elexifier is an app that allows you to transform XML and PDF dictionaries into an *Elexis Data Model* compliant format. Note that the app is currently in a *Public Beta* release and it is likely that you will encounter bugs and/or unwanted behaviour. For assistance, don't hesitate to contact <elexifier@ijs.si>.

---
# Login
Elexifier is available on [elexifier.elex.is](elexifier.elex.is). You can create a user account or login with your *Sketch Engine* credentials.
Once you have logged in, you will be able to choose the XML or the PDF transformation.
<!-- ADD MAYBE SCREENDUMP OPENING SCREEN -->

---

# Table of contents

<!-- vscode-markdown-toc -->
* 1. [XML transformation](#XMLtransformation)
	* 1.1. [Upload a new dictionary](#Uploadanewdictionary)
	* 1.2. [Transform the dictionary](#Edittransformation_OR_Transform_the_dictionary)
<!--		* 1.2.1. [Overview](#Overview) -->
		* 1.2.1. [Adding core elements](#Addingcoreelements)
		* 1.2.2. [Editing core elements](#Editingcoreelements)
<!--		* 1.2.3. [Selecting XML elements](#SelectingXMLelements) -->
		* 1.2.3. [Examples](#Examples)
		* 1.2.3. [Best practices](#Best practices)
	* 1.3. [Download transformed dictionary](#Downloadtransformeddictionary)
<!--	* 1.4. [Removing transformations](#Removingtransformations) -->
<!--	* 1.5. [Resetting transformations](#Resetingtransformations) -->
<!--	* 1.6. [Deleting dictionaries](#Deletingdictionaries) -->
<!--	* 1.7. [7. Editing dictionary metadata](#Editingdictionarymetadata) -->
* 2. [PDF transformation](#PDFtransformation)
	* 2.1. [Sending dictionary to Lexonomy for annotation](#SendingdictionarytoLexonomyforannotation)
	* 2.2. [Annotating dictionary](#Annotatingdictionary)
	* 2.3. [Starting machine learning](#Startingmachinelearning)
	* 2.4. [Previewing results and downloading dictionary](#Previewingresultsanddownloadingdictionary)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

---


---

##  1. <a name='XMLtransformation'></a>XML transformation
The XML transformation consists of three steps:
* 1.1. [Upload a new XML dictionary]
* 1.2. [Transform the dictionary]
* 1.3. [Download the transformed dictionary]

###  1.1. <a name='Uploadanewdictionary'></a>Upload a new dictionary
![](images/new-dict-link.png)

Click NEW DICTIONARY in the bottom left corner of the app.

![](images/new-dict.png)

A pop-up window appears where you can:
1. Upload your dictionary.
<!-- LAYOUT -->
You can drag the file you want to upload in the upload box with the dashed line or you can use the choose button to go to the correct folder on your computer and choose the file you want to upload.

**Note**: Make sure you upload a well-formed XML file. <!-- ADD You can check the well-formedness of you file by ... -->

2. Define its metadata.
3. Enter the basic parameters for the transformation:
- ENTRY ELEMENT: the XML element denoting entries (see Elexis Data Model)
- HEADWORD ELEMENT: the XML element denoting headwords (see Elexis Data Model)
- TRANSFORMATION NAME: select a name for your transformation

**Note**: XPATH notation is used. <!-- ADD EXAMPLE OD SIMPLE PATH AND ONE WHERE YOU NEED TO SPECIFY ENTRY/HEADWORD + POINTER TO SOME MORE COMPLEX CASES, IE. THE HEADWORD IS AN ATTRIBUTE IN THE ENTRY TAG -->

**Note**: The ENTRY and HEADWORD parameters will be used for the initial segmentation of your dictionary. The current version of Elexifier does not support subsequent re-segmentation according to different values of the ENTRY and HEADWORD parameters. If you want to change the segmentation, create a new transformation.
<!-- ADD  AN EXPLANATION FOR THE OPTION CREATE FROM TRANSFORMATION -->

If your upload is successful, you will see the following screen, divided into three panes. Going from left to right, you see the XML dictionary/dictionaries in your account. By clicking on the three dots behind the ditionary file name, you can delete the dictionary or you can edit the metadata. In the next pane, you see the transformation(s) associated with the dictionary you are currently transforming and in the right pane you see a preview of your data. In the top row, four options are offered: you can download your transformed dictionary, you can edit the transformation or you can reset or remove your transformation.
We start with editing the transformation.
<!-- WHAT HAPPENS EXACTLY WHEN YOU RESET THE TRANSFORMATION = RESET TO UPLOAD VALUES? -->
<!-- ADD SCREENDUMP -->
![](images/top-row.png)
---

###  1.2. <a name='edittransformation'></a>Transform the dictionary

To transform your dictionary, click **Edit** in the top row. This will open the Edit Transformation screen.
![](images/edit-screen.png)

The Edit Transformation screen consists of:
- The list of entries on the left hand side. 100 entries are displayed by default and you can search for additional entries using the search box.
- The preview pane showing the *Before* and *After* state of the dictionary. You can use the **Strip namespaces** and **Strip dictScrap** checkboxes for easier to read preview of the transformed dictionary.
- The Transformation editing pane where you can further define your transformation. By default, the elements ENTR, HEADWORD and SENSE are already selected. In the following subsections, we explain how you can add more core elements to your transformation and edit them.

---

####  1.2.1. <a name='Addingcoreelements'></a>Adding core elements
![](images/add-core-element.png)

Click ADD CORE ELEMENT at the top and select one, or click on an existing core element.

---

####  1.2.2. <a name='Editingcoreelements'></a>Editing core elements
![](images/edit-core-element.png)

To edit a core element select an XML element from the list or define a custom path.

<!-- REMOVE? ####  1.2.4. <a name='SelectingXMLelements'></a>Selecting XML elements -->
Elexifier helps you with the selection of XML elements by validating paths and providing suggestions. Start by selecting one of the XML elements from the list (you can type a few characters to filter the list) and then use the up and down keys to select one of the suggested sub-elements. Confirm selection by pressing the Enter key.

![](images/xml-suggestions.png)

**NOTE:** The elements search is case-sensitive.
Once you are happy with the path that you have defined, click **Update** in the top-right corner to update the transformation. See [<a name='Asimpletransformation'></a>A simple transformation].

#### 1.2.3. Advanced editing options
1. Optionally, use **EXCL.** to define the element which should not be included in the transformed dictionary. See [<a name='Excludeelements'></a>Exclude elements]
2. You can join elements to transform multiple XML elements in the input into one core element. See [<a name='Joinelements'></a>Join elements]
2. Select the value to be included in the transformed dictionary:
    - **Element inner text**: extract the inner text of the element
    - **Subtree text**: extract the inner text of the element and all of its descendants
    - **Attribute value**: extract the value of the selected attribute.
    See [<a name='Usingattributevaluesinthetransformeddictionary'></a>Using attribute values in the transformed dictionary]
    - **Constant**: return a constant value instead of extracting the value from the XML
<!-- ADD EXAMPLES FOR ALL THESE OPTIONS -->
3. Optionally, run regex expressions on the extracted values.
<!-- ADD EXAMPLE -->
4. Click **Update** to update the transformation.

---

<!-- REMOVE OLD ####  1.2.4. <a name='SelectingXMLelements'></a>Selecting XML elements -->

<!-- Elexifier helps you with the selection of XML elements by validating paths and providing suggestions. Start by selecting one of the XML elements from the list (you can type a few characters to filter the list) and then use the up and down keys to select one of the suggested sub-elements. Confirm selection by pressing the Enter key. -->

<!-- ![](images/xml-suggestions.png) -->

<!-- **NOTE:** The elements search is case-sensitive.-->

####  1.2.4. <a name='Examples'></a>Transformation Examples
This section contains example transformations that ilustrate the various options offered by Elexifier.

---

##### 1.2.4.1. <a name='Asimpletransformation'></a>A simple transformation
Let's transform a simple XML element `hw` into its Elexis Data Model representation:

    <hw>babble</hw>

Define the HEADWORD element as shown below and press **Update**:

![](images/edit-core-element.png)

The transformed dictionary looks like this:

    <form type="lemma">
        <orth m:e="hw">babble</orth>
      </form>

---

##### 1.2.4.2. <a name='Usingattributevaluesinthetransformeddictionary'></a>Using attribute values in the transformed dictionary
Let's say we want to transform attribute values into Elexis Data Model elements.

    <Lemma writtenForm="X ray" partOfSpeech="n"/>

In the example above, the HEADWORD element can be found in the `writtenFrom` attribute. Start by defining the element containing the attribute to transform (in our case `Lemma`). Then select **Attribute value** in the VALUE field and enter the attribute name (in our case `writtenForm`).

![](images/attribute.png)

The transformed dictionary looks like this:

    <form type="lemma">
        <orth>X ray</orth>
    </form>

---

##### 1.2.4.3. <a name='Excludeelements'></a>Exclude elements
Let's say we have a `tr` element that can denote a headword translation and an example translation. The transformation needs to take into account where the `tr` element appears in the original XML. We can achieve this by using the **EXCL.** option.

    <tr>žlobudranje; blebetanje, čvekanje, kvasanje; <ic>o otroku</ic>čebljanje;<ic>npr. o potoku</ic>žuborenje, šumenje</tr>
    <e>
      <le>the distant babble of women's voices</le>
      <tr>oddaljeno žensko žlobudranje</tr>
    </e>

If we were to use just the `tr` element in the HEADWORD TRANSLATION core element, the resulting dictionary would not be transformed correctly.

![](images/excl-3.png)

In the example below, the `e/tr` element, which denotes a translation of an example sentence, is also transformed into a headword translation.

    <cit type="translationEquivalent">
        <quote xml:lang="sl">žlobudranje; blebetanje, čvekanje, kvasanje; čebljanje; žuborenje, šumenje</quote>
    </cit>
    <cit type="example">
        <quote>the distant babble of women's voices</quote>
    </cit>
    <cit type="translationEquivalent">
        <quote>oddaljeno žensko žlobudranje</quote>
    </cit>


By defining the **EXCL.** parameter, we can prevent the `e/tr` element from being incorrectly transformed into HEADWORD TRANSLATION.

![](images/excl-1.png)

In the EXAMPLE TRANSLATION core element, we can then define the correct path for the example translation:

![](images/excl-2.png)

This results in the correct transformation:

    <cit type="translationEquivalent">
        <quote xml:lang="sl">žlobudranje; blebetanje, čvekanje, kvasanje; čebljanje; žuborenje, šumenje</quote>
    </cit>
    <cit type="example">
        <quote>the distant babble of women's voices</quote>
    </cit>
    <cit type="translation">
        <quote xml:lang="sl">oddaljeno žensko žlobudranje</quote>
    </cit>

---

##### 1.2.4.4. <a name='Joinelements'></a>Join elements

You can transform multiple XML elements into one Elexis Data Model core element. The following dictionary uses `s1` and `s2` to denote senses:

    <s1>
        <hg st="3">
        <ps>sam.</ps>
        </hg>
        <tr>blejanje, beketanje</tr>
    </s1>
    <s1>
        <hg st="4">
        <ps>nepreh. glag.</ps>
        </hg>
        <s2>
        <tr>blejati, beketati</tr>
        </s2>

Define the SENSE core element as follows:

![](images/union.png)

Both elements are transformed as senses:

    <sense xml:id="sense_2">
        <gramGrp>
        <gram type="pos">noun</gram>
        </gramGrp>
        <cit type="translationEquivalent">
        <quote xml:lang="sl">blejanje, beketanje</quote>
        </cit>
    </sense>
    <sense xml:id="sense_3">
        <gramGrp>
        <gram type="pos">nepreh. glag.</gram>
        </gramGrp>
        <sense xml:id="sense_4">
        <cit type="translationEquivalent">
            <quote xml:lang="sl">blejati, beketati</quote>
        </cit>
        </sense>

---
####  1.2.5. <a name='Best practices'></a>Some best practices
This section contains a few best practices for editing your transformation.
<!-- WHAT ELSE SHOULD WE MENTION HERE? -->

##### 1.2.5.1. <a name='Addlanguage'></a>Add language
The **Entry**, **Headword Translation** and **Example Translation** have a dedicated **Language** field where you can select and ISO 639-2 language code. Simply start typing and then select a value from the list.

![](images/language.png)

The resulting dictionary looks like this (note the `xml:lang` attribute):

    <cit type="translationEquivalent">
        <quote xml:lang="slv">blejanje, beketanje</quote>
        </cit>

**Recommendation** Add language to these three elements in your transformation. 

---

##### 1.2.5.2. <a name='Editpart-of-speechcoreelement'></a>Edit part-of-speech core element

The part-of-speech core element is unique among core elements, because you have to specify an additional mapping table for each value found in the part-of-speech element of the original XML file. In the example below, the `ps` element contains the POS information.

    <ps>sam.</ps>

![](images/pos-1.png)

Start by definng the original XML file part-of-speech element and its value as usual.

![](images/pos-2.png)

Click the arrow next to POS and select a value from from the list.

![](images/pos-3.png)

On the right-hand side, select a corresponding Universal Dependency tag.

The transformed dictionary looks like this:

    <gramGrp>
        <gram type="pos">noun</gram>
    </gramGrp>

**Recommendation** Map the part of speech tags in the input to the corresponding tags in Universal Dependencies.

---

###  1.3. <a name='Downloadtransformeddictionary'></a>Download transformed dictionary
![](images/top-row.png)

To download the transformed dictionary, click the **Download** button in the top row.

![](images/download.png)

In the window that opens, you can select to download the dictionary:
- **With namespaces**, which keeps the information on the original xml elements
- **Without namespaces**, which discards the information on the original xml elements
The processing starts in the background. Once it is done, you will see a **Download** button which you can use to download the transformed dictionary.

![](images/download-ready.png)


---
<!-- SEPARATE SECTION NOT NECESSARY
###  1.4. <a name='Removingtransformations'></a>Removing transformations
![](images/top-row.png)

Click **Remove** in the top row. 
-->

---
<!-- SEPARATE SECTION NOT NECESSARY
###  1.5. <a name='Resettingtransformations'></a>Resetting transformations
![](images/top-row.png)

Click **Reset** in the top row.
-->
---

<!-- DO WE NEED THESE AS SEPARATE SECTIONS, IS NOW ALREADY MENTIONED WHEN UPLOAD IS SUCCESSFUL 
###  1.6. <a name='Deletingdictionaries'></a>Deleting dictionaries
![](images/delete-dictionary.png)

Click the three dots next to the dictionary name and then click **Delete dictionary**. This will delete the dictionary and all its transformations.

###  1.7. <a name='Editingdictionarymetadata'></a>Editing dictionary metadata
![](images/metadata.png)

Click the three dots next to the dictionary name and then click **Edit metadata**. You can edit the metadata in the popup window.
-->

##  2. <a name='PDFtransformation'></a>PDF transformation

PDF transformation combines human annotation with machine learning to rapidly convert large PDF dictionaries. Users start by annotating a sample of the data in Lexonomy and then Elexifier propagates the annotations to the entire dictionary.

Tips for best results:
- We suggest you delete any pages that do not contain dictionary data, such as title pages, introductions, tables of contents etc. While it won't stop Elexifier from processing your file, it may have an adverse effect the final results.
- The algorithm uses information about font size, font type, position etc. to learn the annotations. As such, it works best on dictionaries that consistently use different fonts for different elements (headwords, examples, part-of-speech tags etc.).
- While the algorithms work well in general, don't expect perfect results, even in the best of cases, a small number of mistakes may need to be manually corrected.
- Machine learning needs a large enough sample of annotated data. Annotate **at least** four (4) pages of the original XML. Smaller samples may still work, but they are more prone to errors. If you annotated at least 4 pages and still encounter errors or the results are not satisfactory, contact <elexifier@ijs.si>.
- Note that this is a public beta release and you are likely to encounter bugs and/or unexpected behaviour.

###  2.1. <a name='SendingdictionarytoLexonomyforannotation'></a>Sending dictionary to Lexonomy for annotation

After uploading a dictionary, click Annotate and wait while the PDF dictionary is converted and sent to Lexonomy (lexonomy.elex.is).
![](images/pdf-options.png)

Click the link that appears and login to Lexonomy. You will need to create an account with the same email address in Lexonomy in order to annotate the file. By default, Elexifier sends the first 20 pages. In rare cases where you need to annotate more than 20 pages, you can use the **+** sign to send another batch of 20 pages to Lexonomy. Once the file is sent to Lexonomy, you can use the **Reset annotations** button to delete all existing annotations and start over.

![](images/lex-link.png)

###  2.2. <a name='Annotatingdictionary'></a>Annotating dictionary

Select your data (i.e. *pages 1-20* below) from the list in Lexonomy and open it for editing.
![](images/lex-view2.png)

Annotate the following elements: `entry`, `headword`, `part of speech`, `sense`, `definition`, `translation`, `example`. Using the mouse, highlight the words that form an individual element and then double-click to select an annotation label from the list.

![](images/lex-highlight.png)
![](images/lex-selection.png)

The annotations will be visible in the preview window. Lexonomy implements a few basic rules to limit the range of possible annotations. A valid entry will have a **green** rectangle, while an invalid entry will have an **orange** rectangle. When you save the annotations (using the **Save** button in the top toolbar), Lexonomy will warn you if your data contains invalid entries.

**IMPORTANT**: Save your work on a regular basis to avoid losing your annotations!

![](images/lex-annotate-rules.png)



###  2.3. <a name='Startingmachinelearning'></a>Starting machine learning

After you finish the annotation, go back to Elexifier and click the **To ML** button to run the training and predicition processes. Depending on the size of the dictionary, it may take a few hours. You can safely close the window in the meantime. Once the process is completed, Elexifier will display a status message informing you about the results.

###  2.4. <a name='Previewingresultsanddownloadingdictionary'></a>Previewing results and downloading dictionary

You can check the results of the prediction process in Lexonomy. After ML is finished, click the **To Preview** butoon to send the file back to Lexonomy and have a look at the results. If you are happy with the results, click **Download** in Elexifier to download a TEI-compliant XML file of the converted dictionary. 

Due to various types of PDF file encodings, the initial PDF conversion can contain corrupted characters. If this is the case in your data, you can map corrupted characters to proper ones using the **Map characters** button. 
