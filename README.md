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

A Brain Brew recipe is run in the command line with `brainbrew run [recipe]` and takes a recipe file as an argument. 

> brainbrew run recipes/source_to_crowdanki.yaml

Two sets of these recipes are provided in this repo under `recipes/`, each having their own export folder in `build/`.


1. One which just converts normal words inside `src/data/words.csv` into a single note type.

1. And another that does the same, but also uses the extra 'derivative' files `nouns.csv` and `verbs.csv` 
   to add extra fields to certain entries in the `words.csv`.

Each set contains a recipe to convert *from* or *to* a CrowdAnki file.


## Setting up your own cards for Import/Export

Change this repo to support your own flashcards! Simply follow these steps:

1. Delete the following folders in this repo:
   1. `/build`
   1. `/recipes`
   1. `/src`

1. Export your deck using CrowdAnki and place that export somewhere accessible
   
1. In the command line while in the main folder of this repo run `brainbrew init [Your CrowdAnki Export Folder]`
   - This will generate the entire repo for you, including the recipe files, source files, and build folder

1. Run `brainbrew run recipes/source_to_anki.yaml` to generate the deck in the `/build` folder

Now you have a fully working repo :clap: If you experience any errors during this process,
please [open an issue](https://github.com/ohare93/brain-brew/issues) (if one does not already exist).

This init command is not smart when it comes to pairing note to use advanced features such as
csvs derivatives shared note model templates/styling.
It simply just gives you a working base, which can then be customised to a more advanced setup! :thumbsup: 

#### Source -> Anki
The deck in `/build/deck.json` should be identical to your original deck.
Make changes in the csv files and run `source_to_anki` to update the crowdanki file.

#### Anki -> Source
Or make changes in Anki and export it back into source here by overwriting `build/deck.json`
with a CrowdAnki export and run `anki_to_source` recipe to pull data back from


## Making new cards

Simply add a value into a setup csv and run brain-brew with Csv to CrowdAnki! 
**You do not need to fill in the guid**, that will be automatically generated.

Alternatively, create a card in Anki and sync the changes back through into the csv. 
Use the power of git change compare to find what you need to keep.

# Questions

If there is anything I have left out, or that could be clearer, 
*do not hesitate to open an issue or discussion* in either this repo or Brain Brew itself :+1:

Thanks! :100: :rocket: