# XML Forms Special Meeting

## May 5, 2015

Call details: Skype

## Agenda

1. Expanded discussion on [Islandora 7.x-2.x Issue 28](https://github.com/Islandora-Labs/islandora/issues/28).

## Participants

* Andy Wagner (UofT)
* Kim Pham (UTSC)
* Lingling Jiang (UTSC)
* Jared Whiklo (University of Manitoba)
* Chuck Schoppet (USDA)
* Melissa Anez (Islandora Foundation)
* Nick Ruest (York University)
* Danny Lamb (dgi)
* Robin Dean (Colorado Alliance of Research Libraries)
* Mark Jordan (SFU) :star:

## Notes

Focus on https://github.com/Islandora-Labs/islandora/issues/28

* Danny: Xpath Field module works well for display, but doesn't write content to XML fields. jquery.xmleditor and doctored.js would need a lot of work to function within Drupal. Form Builder is still a real possibility but there are sustainabilty issues.

* Robin asked how Hydra allows editing of XML binaries. Nick responded that there is no single way that they handle metadata. We know that we need MODS plus any other metadata schemas that exist in the Islandora. MODS-RDF is not a viable option at this time.

* Long passionate discussion about treating XML Form Builder as an integral component and not a "utility module." This is an organizational issue, not a technical issue.

* Option of moving the form <-> XML translation to the middleware. Robin points out that we need to be able to keep doing bulk XML metadata ingests, and the middleware approach would accommodate this. Also that we need to be able to customize transformation and not need to rely on the LoC transformations.

* Use case of having a general XML editor, not just a descriptive metadata-specific solution.

* Technical metadata will be properties on a file, but we'll still need to accommodate a FITS datastream/binary file (for example). See Hydra [Technical Metadata Application Profile](https://wiki.duraspace.org/display/hydra/Technical+Metadata+Application+Profile).

* Chuck described how the USDA Agricultural Library uses Form Builder to heavily.

* Robin nailed it: "In Fedora 4 we will need to be able to create XML, edit it, transform it, and index it". Many thumbs were raised to support this general use case. Lots of support for making a business case for sustaining Form Builder.

* Action item: Nick to create a Google Doc to gather feedback to determine which features are must-have and which are not used: [Islandora XML Forms 2.x -- Functional requirements](https://docs.google.com/document/d/1zkyy40v4lz03rpjpmVHWujU9LQcxrsA4EC75D1d7X7A/edit?usp=sharing)

* Danny brought up the question of whether we edit RDF triples in (a version of) Form Builder. Lots of discussion but we need to address this question before we move ahead on adopting FB as our XML editor.
