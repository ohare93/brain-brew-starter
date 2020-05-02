# Brain Brew Starter

A full working repo using [Brain Brew](https://github.com/ohare93/brain-brew) :+1: Easy to clone and change to use your own cards.

## Install steps 

1. Clone or fork repo
1. Create a new pipenv using the provided Pipfile with `pipenv install`. This will install [Brain Brew from PyPi](https://pypi.org/project/Brain-Brew/) and it's requirements.
(Note, you can simply run `pip install brain-brew` instead if you wish, but a virtual environment is recommended)


## Running Brain Brew

Brain Brew is run in the command line with `brain-brew` and takes a builder config as an argument. Two of these config files are provided in this repo under `builder_configs/`

`brain-brew builder_configs/csv_to_crowdanki.yaml`

This will convert the csv `words.json` into a crowdanki export `General/`. The config file itself contains a general explanation of the key values necessary.

#### Run in Reverse
Use `-r` or `--reverse` in the cmd to flip the direction of the conversion, or specify it inside the build config itself.


## Importing your own cards

Here are the steps to take to import your own cards into this repo:

1. Export your cards from Anki with the latest version of CrowdAnki and place the resulting folder somewhere in the repo. I recommend setting a `note_sort_order` of `"note_model_name, guid"` inside the CrowdAnki settings first.
1. Make sure the builder file you wish to use is pointing to your CrowdAnki export folder.
1. Run brain-brew of CrowdAnki to DeckParts. The fastest way to do this is to use one of the provided builder_config files using `-r` for reverse.
1. Create a csv with the necessary columns from your note_model (or edit one here to match). Running DeckParts to Csv may fail, but the error message will state which columns you are missing still. Make sure the `note_model_mapping` inside the build config is configured correctly so that all columns in the csv and fields in the note model are covered.
    1. If you have multiple note types you will currently need multiple csvs, each representing one note model.
    1. If some of your note models are "derivatives" of another (they contain the exact same fields as a parent, plus some extra) then see the provided `csv_to_crowdanki_with_derivatives` builder file on how to map csvs together as derivatives.
1. You should now have a fully running config resulting in CrowdAnki export to csv. Manually change a field value in the CrowdAnki export and run it again to confirm the value in the csv updates.
1. Run it the other way! You can do so with `-r` or make a separate build file for that task. Again make a change and confirm it comes through to the CrowdAnki export.


## Making new cards

Simply add a value into a setup csv and run brain-brew with Csv to CrowdAnki! You do not need to fill in the guid, that will be automatically generated.

Alternatively, create a card in Anki and sync the changes back through into the csv. Use the power of git change compare to find what you need to keep.

### ReadMe Todo
1. GlobalConfig File "brain_brew_config.yaml"
    1. Specifying the config file via the command line
1. Media files
1. Csv specifics
    1. Derivatives specifics
    1. Required columns guid and tags
1. Change control - what should be in it? General answer: whatever you personally want!
1. Personal Fields (soon:tm:)
1. Non-Existant Files Cannot Be References! If you want to make a new DeckPart make a copy of an existing one and write over it, or make a blank json file with `{}` as the contents.