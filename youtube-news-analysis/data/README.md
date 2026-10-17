# Data

| File | Rows | Description |
|---|---|---|
| `videos.csv` | ~200 | One row per video: channel, title, views, likes, comments, publish date, duration, URL |
| `comments.csv` | ~4,400 | One row per comment: video ID, text, like count, date, parent comment ID (for replies) |

## Collection

- Source: YouTube Data API v3 (`search.list`, `videos.list`, `commentThreads.list`)
- Query: video titles containing `coronavirus`, `covid`, `covid-19` or `pandemic`
- Channels: BBC News, CNN, Fox News, MSNBC
- Date range: 2020-01-01 to 2023-01-01
- Up to 50 videos per channel

## Collection notes

- Comments: first page of comment threads per video (about 20, newest first), plus the first page of replies to each. 4 videos had comments disabled.
- Text was pre-processed at collection time: video titles and comment text are lowercased, with punctuation and digits removed. Comments also had English stopwords removed and non-English comments filtered out.
- `duration` is stored in ISO 8601 format (e.g. `PT4M13S`) and converted in the notebook.

## Privacy

The `comment_author` column has been removed from `comments.csv` before publishing, since commenter names aren't needed for the analysis.
