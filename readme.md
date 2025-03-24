# Guide to this repository
Python lets you create 'notebooks' which is a file containing markdown ( like a word document ) and code itself ( in modular code blocks that can be ran in any order )


## installation
1. make sure python3.11 or honestly any python im pretty sure is installed
  - if not go to their website at python.org and download
  - make sure path option is checked when installing

2. clone the repo -> open a terminal window

( extra step not necessary ) `mkdir ~/projects && cd ~/projects`

`git clone https://github.com/xavierwallis/prophet-api-data.git prophet-api-data`
'cd prophet-api-data'

3. open your terminal and type
  `pip install notebook`
  - if you get 'pip not found' contact me you have to make pip an entry in your path

4. within same terminal window type
`jupyter notebook`
- it should say a local instance is running at http://localhost:8888
  visit this site in your browser and you should have an entry into the entire folder

5. you should see prophet-api-data.ipynb in the list, double click and open and you should see all of the code blocks and markdown

## Jupyter notebooks
code with ! infront like !pip install just runs shell commands
shift+enter to run a code block
hover in between blocks to insert either markdown or code
if a variable is the only thing in the last line of a code block it displays info about the variable for inspection

# TLDR run on mac (shove into terminal window havent tested so good luck lol)
```
if (( $+commands[brew] )); then
  echo "brew satisfied"
else
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  cd /opt/homebrew/bin/
  PATH=$PATH:/opt/homebrew/bin
  echo export PATH=$PATH:/opt/homebrew/bin >> ~/.zshrc
  cd -
fi

if (( $+commands[git] )); then
  echo "git depenency resolved"
else
  brew install git
fi


if (( $+commands[python3] )); then
  echo "python3 installed"
else
  brew install python3
fi

if (( $+commands[jupyter] )); then
  echo "jupyter stalified"
else
  pip install notebook
fi

mkdir ~/projects && cd ~/projects/
git clone https://github.com/xavierwallis/prophet-api-data.git prophet-api-data && cd prophet-api-data

jupyter notebook
```

# The code explanation
retreiving the token and url based on the .env file (just a nice way to hold them all) but you can hardcode if makes more sense as well

I set up that game time per the spec on the api docs

python lets you send web requests ( used by apis to communicate )
by the requests package

I send a request with the correct headers, specifying content type and authorization token

I take this data and load it into a <bold>pandas</bold> dataframe, more info can be found on google it is effectively a more powerful google sheet

### to note
the operations performed may seem intimidating, this is why code blocks are helpful, I didnt just magically come to these but instead kept testing the data by use of the code blocks.
some advice to learn would be to take the most basic part of the line and run in a sepereate block to see what it looks like, add a bit more of the line and see what that data does: for example

\$`foo: str = 'hi there'`  
\$ `foo`  
\> hi there  
\$ `foo[::-1] # reverses the string`  
\> ereht ih  

also if unsure select and ship to chatgpt can explain probably better than I can

### ONWARD
anyhoo i take data do manipulations to get each event for a day and then the moneyline for each event

prophet is weird and has multiple spreads and multiple totals for each event so left that alone didnt know how you wanted to handle that

good luck! lmk if need anything