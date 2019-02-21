## Gabber - data-analysis tools for gab.ai

This repository aims to provide a set of tools for data-driven media studies on the gab.ai platform.

### Requirements

These tools require python3 and access to a MongoDB server.
On a debian system, run:

    sudo apt-get install python3-pymongo mongodb-server

### Scraping

The minegab.py script is meant for scraping data from the gab.ai platform. All scraped data is stored in MongoDB for further parsing/analysis.

#### Usage

Scraping data from gab.ai starts at a particular account, whose username has to be manually provided to the script:

    ./minegab.py -u <username>

From there, the script will discover other accounts through reposts, follow-relations, comments, and quotes.
Once the first account has been processed, the -a parameter will tell the script to scrape data from all the discovered accounts. In doing so, more accounts will likely be discovered:

    ./minegab.py -a

Keep running the script with -a untill no new accounts are discovered. The giant graph within gab.ai has now been scraped.
The minegab.py will give verbose output with the -d flag. Note that this might contain special characters that could be problematic to print on your terminal:

    export PYTHONIOENCODING=UTF-8
    ./minegab.py -da

#### Limitations

The minegab.py script can not scrape beyond the giant graph of which the manually provided accounts are a part. It will not find other communities if they are completely isolated from the accounts provided to the script.

Furthermore, the minegab.py script does not retrieve any media content. It will store links to media assets in the database, which could be used as an input for a downloading script, but this functionality is not provided by the script. Note that scraping all media content will require considerable bandwidth and storage capacity.

Finally, the 'news' and 'groups' sections of gab are ignored entirely.


### Processing

TBD.
