# User Guide for Concept Recognition Annotation

## Save & Pause your annotation session:

Never forget to glick the save-icon before closing the annotation-we-page! 
Otherwise You have to do all the annotations again.

![img.png](data/img_save.png)

If you want to do a brake, hit the save icon and close the web-browser. 
If you open your annotation-web-page again, it will continue where you left.

## Two Annotation phases

Our KBC-concept recognition pipeline works like this:

![img.png](data/img.png)

So we have 2 annotation phases:

## Phase 1) NER-Annotation:

First, we have a NER (Named Entity Recognition) Phase, where we simply search entities (_medical terms_) in the texts.
It is a binary NER model which simply marks sections in the texts, which might be a medical concept.

![img_ner.png](data/img_ner.png)

Each sentence of a report is presented to the annotator one after the other. Each presented sentence is already pre-annotated by a simple NER model.

The annotator has to check the pre-annotated sentence and correct it if necessary.
Make sure that all medical terms in the sentence are marked at the end. 

## NER-Annotation-Rules:

- Do not highlight numbers, but please highlight codes like ICD's or tumor stagings.
- Please highlight each medical term, also the ones which are not present in the KBC or SNOMED or any other terminology.
- prefer longer, combined medical terms over shorter ones.
  - e.g.prefer _[scarred globally]_ = one entity over _[scarred] [globally]_ = 2 entities.
  - reason: The chance that the KBC-concept-linker finds a fitting KBC concept is higher for longer entities.

## Behavior of the buttons in the web interface:

These are the buttons of the web interface:

![img_buttons.png](data/img_buttons.png)

From left to right: Accept, reject, ignore and undo.

As soon as you have marked all medical terms in the text, click on the green "accept" button. After that, the next sentence is presented to you.

If something is wrong with the proposed sentence, click on the red "reject" button.

Never click the "ignore" button.

If you want to re-edit a previously annotated sentence, click on the undo button to drop the current annotated sentence and go back to the previous one.

## Phase 2) NEL-Annotation:

Second, we have a NEL (Named Entity Linking) or EL (Entity Linking) Phase. 
In this phase, we select one concept from the given terminology (in this case: KBC) for each highlighted medical term/entity.

![img_nel.png](data/img_nel.png)

For each marked text excerpt, the KBC terminology is searched for KBC concepts that could match to it. 
The KBC concepts that might fit best (according to GPT) are offered in the web interface.

if there is a well-fitting KBC concept, but it is not listed in the web interface, 
the concept must be entered manually, in the text field below.

If the terminology does not contain any concept that fits to the given text excerpt, 
 click on accept without selecting one of the suggested concepts. 
(or click on reject, it doesn't really matter?).

