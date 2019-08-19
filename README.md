# WikiInfo2Text
This repo hosts the data used in paper "Enhancing Neural Data-To-Text Generation Models with External Background Knowledge (Chen et al., 2019)"

This dataset is an extension of previous [WikiBio dataset](https://github.com/DavidGrangier/wikipedia-biography-dataset) where we extend previous single Biography domain to other twenty domains (e.g. Album, Book etc.) and we augment the infobox with external knowledge from [WikiData](https://www.wikidata.org/wiki/Wikidata:Main_Page).


 Totally, we have 21 infobox categories (WikiBio + 20 self-collected categories). Each instance is equipped with:
* Infobox: in the format of (field, value) pairs
* Reference: The sentences in corresponding Wikipedia article
* KB: External knowledge expanded from Infobox via hyperlink, we retrieve one-hop fact tuples from [WikiData](https://www.wikidata.org/wiki/Wikidata:Main_Page). We describe each fact using ID representation (entities and relations are denoted with WikiData [ItemID](https://www.wikidata.org/wiki/Help:Items) and [PropertyID](https://www.wikidata.org/wiki/Help:Properties)) and String representation (entities and relations are denoted with Item name and Property name)
### Example
Below is one example titled [Raiders of the Lost Ark (soundtrack)](https://en.wikipedia.org/wiki/Raiders_of_the_Lost_Ark_(soundtrack)) from [Album](https://en.wikipedia.org/wiki/Template:Infobox_album) category.
The data is in json format.
```json
{
  "Sentences": [
    "The soundtrack to \" Raiders of the Lost Ark \" was released by Columbia Records in June 1981 .",
    "The music was composed and conducted by John Williams , and performed by the London Symphony Orchestra .",
    "Orchestrations were done by Herbert W. Spencer with additional orchestrations done by Al Woodbury ."
  ],
  "name": "Raiders of the Lost Ark",
  "type": "Film score",
  "artist": "\" Indiana Jones \"",
  "cover": "Raiders soundtrack.jpg",
  "released": "June 1981",
  "recorded": "February 1981",
  "genre": "Soundtrack",
  "length": "43:00",
  "label": "PolyGram , DCC Compact Classics/Sony Music Special Produtcts , Columbia Records ( Original LP Release )",
  "producer": "",
  "chronology": "",
  "last_album": "",
  "this_album": "\" Raiders of the Lost Ark \"",
  "next_album": "\" Indiana Jones and the Temple of Doom \"",
  "misc": "Extra chronology",
  "articletitle": "Raiders of the Lost Ark ( soundtrack )",
  "KB_id_tuples": [
    [ "genre", "Q217199", "P279", "Q2188189" ],
    [ "genre", "Q217199", "P910", "Q5623792" ],
    [ "label", "Q700359", "P156", "Q38903" ],
    [ "label", "Q700359", "P112", "Q1536003" ],
    [ "label", "Q700359", "P31", "Q18127" ],
    [ "label", "Q700359", "P127", "Q38903" ],
    [ "label", "Q183387", "P31", "Q18127" ],
    [ "label", "Q183387", "P31", "Q783794" ],
    [ "label", "Q183387", "P127", "Q330629" ],
    [ "label", "Q183387", "P910", "Q15099822" ],
    [ "label", "Q183387", "P17", "Q30" ],
    [ "label", "Q183387", "P136", "Q8341" ],
    [ "label", "Q183387", "P749", "Q330629" ],
    [ "next_album", "Q6023297", "P31", "Q482994" ]
  ],
  "KB_str_tuples": [
    [ "genre", "soundtrack", "subclass_of", "musical_work" ],
    [ "genre", "soundtrack", "topic_'s_main_category", "Category_:_Soundtracks" ],
    [ "label", "PolyGram", "followed_by", "Universal_Music_Group" ],
    [ "label", "PolyGram", "founded_by", "Philips_Records" ],
    [ "label", "PolyGram", "instance_of", "record_label" ],
    [ "label", "PolyGram", "owned_by", "Universal_Music_Group" ],
    [ "label", "Columbia_Records", "instance_of", "record_label" ],
    [ "label", "Columbia_Records", "instance_of", "company" ],
    [ "label", "Columbia_Records", "owned_by", "Sony_Music_Entertainment" ],
    [ "label", "Columbia_Records", "topic_'s_main_category", "Category_:_Columbia_Records" ],
    [ "label", "Columbia_Records", "country", "United_States_of_America" ],
    [ "label", "Columbia_Records", "genre", "jazz" ],
    [ "label", "Columbia_Records", "parent_organization", "Sony_Music_Entertainment" ],
    [ "next_album", "Indiana_Jones_and_the_Temple_of_Doom", "instance_of", "album" ]
  ]
}
```
As you can see, the basic fields like *type*, *artist*, *released* etc. state basic information in the infobox. The field *Sentences* is the reference sentence. The external knowledge from Wikidata is given in *KB_id_tuples* and *KB_str_tuples* fields. Each tuple is list of four elements eg. (["genre", "Q217199", "P279", "Q2188189"]). The elements [*Q217199*](https://www.wikidata.org/wiki/Q217199), [*P279*](https://www.wikidata.org/wiki/Property:P279) and [*Q2188189*](https://www.wikidata.org/wiki/Q2188189) are the subject, relation and object of the fact respectively, and field name *genre* indicates the fact is expanded from this field in infobox.

### Download
[Click here](https://drive.google.com/drive/folders/1H0AZ23sY3W6e2EsXeJ30PCANl1rTZMjU) to download the data.

### Licence
License information is provided in [License.txt](https://github.com/hitercs/WikiInfo2Text/blob/master/LICENSE.txt)
