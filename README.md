# espnscrapeR_data
Data repo companion to my [`{espnscrapeR}`](https://jthomasmock.github.io/espnscrapeR/) package.

# nflfastR-data
NFL play-by-play data scraped from the [`nflfastR` package](https://github.com/mrcaseb/nflfastR) going back to 1999. Each season contains both regular season and postseason data, with `game_type` or `week` denoting which.

Data are stored in the data folder, available as either compressed csv (.csv.gz) .rds, or .parquet.

**Note that for much of this data, you can join against `nflfastR` via Lee Sharpe's [nfldata repo](https://github.com/leesharpe/nfldata)**

If you're looking for general NFL data, check out Lee's [NFL Game Data site](http://nflgamedata.com/schedule.php).

For `nflfastR` proper, you can find it on [Github](https://github.com/mrcaseb/nflfastR). 

There's also the [rbsdm.com](https://rbsdm.com/) site that has lots of advanced analytics and boxscores.

___

### Load data using R
If you're using R, you might as well load the data in the binary .rds format. The following example shows how to load the seasons 2010 to 2019 (binded into a single dataframe).

```{r}
# define which seasons shall be loaded
seasons <- 2010:2019
qbr <- purrr::map_df(seasons, function(x) {
  readRDS(
    url(
      glue::glue("https://raw.githubusercontent.com/guga31bb/nflfastR-data/master/data/play_by_play_{x}.rds")
    )
  )
})

```
