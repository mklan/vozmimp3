# vozmimp3
custom scraper API for querying the vozmimp3.com MP3 database

> __Warning:__ https://vozmimp3.com is down, so this service does not work anymore!

## install

`npm install vozmimp3`

## usage

to search for a mp3 title or an artist use the `queryVozmiMp3` method. Provide a data object with key `q` and the value of the query string. Optionally you can limit and sort your results.

```javascript
const vozmimp3 = require('vozmimp3');

const data = {
  q: 'cedar m Planet Of Tokyo',
  limit: 5, //default: 20
  sort: {
    keys: ['duration'], //(duration, title, link) default: title  
    order: ['desc'] //(asc, desc) default: asc
    //hint: you can use multiple keys and corresponding orders
  }
}

vozmimp3.queryVozmiMp3(data).then((result) => {
  console.log(result);
}).catch((err) => {
  console.log(err);
});
```

`getPlaylist` lets you create playlists. Provide a `list` key with an array of search queries. For best results use very specific title searches. The API will return one result per item. You can specify a `strategy` to retrieve the item with the longest duration

```javascript
const vozmimp3 = require('vozmimp3');

const data = {
  list:
  ['cedar m Planet Of Tokyo',
   'Zonderling Sonderling',
   'dj matthiasKlan',
   'Rude 66 - The 1000 Year Storm'
  ],
  strategy : 'longestDuration' //default: first
}

vozmimp3.getPlaylist(data).then((result) => {
  console.log(result);
}).catch((err) => {
  console.log(err);
});
```
