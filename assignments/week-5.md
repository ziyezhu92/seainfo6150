# INFO6150 Week 5 Assignments

## create a list component
Create a new functional component in `ArticleList/ArticleList.js`, with the appropriate valid, semantically-correct containing HTML to create an unordered list.

Your component should use the following block of code to output each of the articles as an ArticleListItem component.

```
{
  // this iterates through the articles JSON and
  // calls your ArticleListItem component for each article
  Object.values(articles).map(article => {
    return <ArticleListItem
      key={article.slug}
      title={article.title}
      date={article.pubDate}
      year={article.pubYear}
      author={article.author}
      shortText={article.shortText}
    />
  })
}
```

The list should be marked up with valid, semantically-appropriate HTML. Consider block level and inline HTML elements, what kind of text this is and how you should properly cite the author, the date, etc.

You should be able to use your `ArticleTable.js` component from week 4 as a basis for `ArticleList.js`.

## create a list item component
Create a new functional component in `ArticleList/ArticleListItem.js` that displays data about each of the news articles in `seainfo6150-webapp/src/data/articles.json` that are being passed as props. **You should not modify `articles.json` in any way.**

The article data should be marked up in the list item with valid, semantically-appropriate HTML. Consider how you should properly cite the author, the date, etc.

ArticleListItem accepts 5 props:
* title: a string
* date: a date string
* year: a year string
* author: a string
* shortText: a string

## style the components
Create styles for the two new components in `ArticleList/ArticleList.module.css` and `ArticleList/ArticleListItem.module.css`. Make sure to import the css into `ArticleList/ArticleList.js` and `ArticleList/ArticleListItem.js` as demonstrated in class using CSS modules. Please style your components to match <a href="./week-5-list-screenshot.png">this screenshot</a> as closely as possible.

## use the component
In `src/App.js`, import and use `ArticleList.js` so that the entire list of articles is displayed on the main app page (http://localhost:3000). Don't forget to pass the articles prop (you should be able to use the `ArticleTable.js` component in `App.js` component from week 4 as a basis for doing this.)

## send me an email!
Send me an email with a link to your github repo
