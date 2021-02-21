# Brain Brew Starter

<a title="Buy me a cuppa tea" href="https://ko-fi.com/brainbrew"><img src="https://img.shields.io/badge/ko--fi-contribute-%23579ebd.svg"></a>
<a title="Support a fellow Weekend Warrior on Patreon" href="https://www.patreon.com/jmohare?fan_landing=true"><img src="https://img.shields.io/badge/patreon-support-%23f96854.svg"></a>

A full working repo using [Brain Brew](https://github.com/ohare93/brain-brew) :+1:
This repo is for demonstration purposes, and gives a user an already working system to morph to fit their own needs.
Though there are currently some difficulties in getting personal Note Models to sync here without the hassle of manual setup,
an easier process should be coming soon:tm:!️

If you get use of out this project, or wish to see it progress, please do consider supporting :pray:

## Install steps 

1. Clone or fork repo
1. Install general requirements
    1. Python 3.7+
    1. Pip
    1. Pipenv
1. Create a new pipenv using the provided Pipfile with `pipenv install`. This will install [Brain Brew from PyPi](https://pypi.org/project/Brain-Brew/) and it's requirements.
(Note, you can simply run `pip install brain-brew` instead if you wish, but a virtual environment is recommended)
    1. Enter the virtual environment with `pipenv shell` if need be, in order to run the next steps.

## Running Brain Brew

Brain Brew is run in the command line with `brain-brew` and takes a recipe file as an argument. 

> brain-brew recipes/source_to_crowdanki.yaml

Two sets of these recipes are provided in this repo under `recipes/`, each having their own export folder in `build/`.


1. One which just converts normal words inside `src/data/words.csv` into a single note type.

1. And another that does the same, but also uses the extra 'derivative' files `nouns.csv` and `verbs.csv` 
   to add extra fields to certain entries in the `words.csv`.

Each set contains a recipe to convert *from* or *to* a CrowdAnki file.


## Importing your own cards

If your cards are simple enough, you should be able to the following to get your cards syncing:

1. Export your deck using CrowdAnki and place that export in the build folder
1. Recipe changes:
   1. Name of the Deck to import (to the deck created above)
   1. Change all the note model
      1. Names
      1. Fields
      1. Templates
   1. Note Model Mapping
      1. Columns_to_fields
1. File changes
   1. Csvs
      1. Column headings
      1. Delete the current data, if desired
   1. Note Model files
      1. Templates
         1. Create new or edit the existing templates
            1. Make sure the question at the top, and the answer at the bottom
            1. Separated by `--` with empty lines before and after
      1. Style.css
         1. Make multiple, or have many note models share the same one
   1. Media
      1. Delete the existing media
1. Run `brain-brew recipes/source_from_crowdanki.yaml -v` to verify the recipe is functional
   1. Then remove the `-v` to run it properly

That should be it. Again, I am working on an easier way to set this up as a normal user :pray: 
      

## Making new cards

Simply add a value into a setup csv and run brain-brew with Csv to CrowdAnki! 
**You do not need to fill in the guid**, that will be automatically generated.

Alternatively, create a card in Anki and sync the changes back through into the csv. 
Use the power of git change compare to find what you need to keep.

# Questions

If there is anything I have left out, or that could be clearer, 
*do not hesitate to open an issue or discussion* in either this repo or Brain Brew itself :+1:

Thanks! :100: :rocket: