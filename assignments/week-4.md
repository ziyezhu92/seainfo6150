# INFO6150 Week 4 Assignments

## update ArticleTableRow component
Update the class component ArticleTableRow that displays data about each of the news articles in seainfo6150-webapp/src/data/articles.json that are being passed as props. **You should not modify articles.json in any way.**

The article data should be marked up in the table with valid, semantically-appropriate HTML. Consider how you should properly cite the author, the date, etc.

Each table row must have these columns in this order:

* column 1: a valid, semantically correct checkbox that calls the onClick handler already in ArticleTableRow.js. Please see the comment about pasting the onClick code into your checkbox.
* column 2: the status of the checkbox, which is stored in the variable selectedStatus ('Yes' or 'No' depending on if the checkbox is checked)
* column 3: the author
* column 4: the date
* column 5: the short text

ArticleTableRow accepts 4 props:
* title: a string
* date: a date string
* author: a string
* shortText: a string

## update ArticleTable component
Update the functional component ArticleTable with the appropriate valid, semantically-correct containing HTML to create a table. Your table must have a table header with named column heads and a caption title. Make sure that your column heads match up with the columns created in the ArticleTableRow component.

You do not have to update the component call or props to ArticleTableRow.

## send me an email!
Send me an email with a link to your github repo.
