# Generating a wordcloud based on the data generated from your Whatsapp chats.

### Prerequisites-
- R (preferably version 3.2.3 or higher)
- A WhatsApp chat in plain text format

### Here's how to get the text data-

- Open up your Whatsapp.
- Open up the chat you wish to parse.
- Tap on the menu button present near the top right of your screen.
- Click on email chat.
- Download the file mailed to your email.
- Replace the path given here with your desired path.

```{r echo = FALSE}
whatsappRaw <- read.table("WhatsApp Chat with CSE Junior Year.txt", header=FALSE,fill = TRUE)
```


```{r include = FALSE}
library(dplyr)
whatsappDF <- tbl_df(whatsappRaw)
head(whatsappDF) 
```

Selecting only the names of the recipients (the data frame is loaded in the form of columns from V1:V20):
```{r eval = FALSE}
select(whatsappDF,V5)
```

The cloud was generated in the following way:
```{r include = FALSE}
library(wordcloud)
```
```{r echo = FALSE}
wordcloud(whatsappDF$V5, random.order = FALSE, max.words = 100, col = brewer.pal(7,"Accent"))
```
![Wordcloud](https://github.com/starship9/whatsappR/blob/master/whatsappR/senderCloud.png)
