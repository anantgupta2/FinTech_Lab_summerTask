## Goal
Use API calls to summarize 10K filings data made available by the US government.

### Downloads
User needs to install following dependencies to run the program locally (we use python):

```
pip install -U sec-edgar-downloader
pip install -q -U google-generativeai
pip install flask
pip install markdown2
```

The first install is for the sec edgar data API
The second install is for the inference prompt for the LLM
The third and fourth install are for the app (which I currently run locally)

### The python files
data_parser.py contains all functions needed seperately. I used human readable primary-document.html insteead of full-submission.txt because I could parse the former one better and the latter contained (in my opinion) data that was unnecessary. This seperation is to resolve any errors that might occur within individual functions. I use the gemini-pro as it is a good chatbot that I have previously used.

I parse the data by choosing only specific sections of the document and feeding them to the LLM. After this, the task was a prompt engineering question and in the end, I first summarized the data for each year and then used those summaries to generate a final summary of the progress of the company. I could probably do better but this was the best option I reached. This was because the initial file was too long and I could not input the whole thing to the LLM itself.


main_functionality.py can be used to test the function without using the app.

app.py contains the app functionality that displays the generated output from the LLM. Put in any ticker and then the speed at which you wish to process and you will get the output.


### Tech Stack
I used python because I am proficient in the language and it is very simple to make API calls usin python. I used Flask for the app because that was the simplest app coding I could find (I am not very familiar with making apps/websites). User may change the structure and deploy their own app using the functions provided. Additional functionality can be added by simply adding a more options in the downloading of the filings.

### Outputs
A few outputs have been stored in the text files for DBX and DASH.

### Google API Key
Please download your own google API key from https://aistudio.google.com/app/apikey.
