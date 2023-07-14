#### nfl_data_py

nfl_data_py is a Python library for interacting with NFL data sourced from [nflfastR](https://github.com/nflverse/nflfastR-data/), [nfldata](https://github.com/nflverse/nfldata/), [dynastyprocess](https://raw.githubusercontent.com/dynastyprocess/), and [Draft Scout](https://draftscout.com/).

Includes import functions for play-by-play data, weekly data, seasonal data, rosters, win totals, scoring lines, officials, draft picks, draft pick values, schedules, team descriptive info, combine results and id mappings across various sites.

### Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install nfl_data_py.

```bash
pip install nfl_data_py
```

## Usage

```python
import nfl_data_py as nfl
```

**Working with play-by-play data**
```python
nfl.import_pbp_data(years, columns, downcast=True, cache=False, alt_path=None)
```
Returns play-by-play data for the years and columns specified

years
: required, list of years to pull data for (earliest available is 1999)

columns
: optional, list of columns to pull data for

downcast
: optional, converts float64 columns to float32, reducing memory usage by ~30%. Will slow down initial load speed ~50%

cache
: optional, determines whether to pull pbp data from github repo or local cache generated by nfl.cache_pbp()

alt_path
: optional, required if nfl.cache_pbp() is called using an alternate path to the default cache

```python
nfl.see_pbp_cols()
```
returns list of columns available in play-by-play dataset

**Working with weekly data**
```python
nfl.import_weekly_data(years, columns, downcast)
```
Returns weekly data for the years and columns specified

years
: required, list of years to pull data for (earliest available is 1999)

columns
: optional, list of columns to pull data for

downcast
: converts float64 columns to float32, reducing memory usage by ~30%. Will slow down initial load speed ~50%

```python
nfl.see_weekly_cols()
```
returns list of columns available in weekly dataset

**Working with seasonal data**
```python
nfl.import_seasonal_data(years)
```
Returns seasonal data, including various calculated market share stats

years
: required, list of years to pull data for (earliest available is 1999)

**Additional data imports**
```python
nfl.import_rosters(years, columns)
```
Returns roster information for years and columns specified

years
: required, list of years to pull data for (earliest available is 1999)

columns
: optional, list of columns to pull data for

```python
nfl.import_win_totals(years)
```
Returns win total lines for years specified

years
: optional, list of years to pull

```python
nfl.import_sc_lines(years)
```
Returns scoring lines for years specified

years
: optional, list of years to pull

```python
nfl.import_officials(years)
```
Returns official information by game for the years specified

years
: optional, list of years to pull

```python
nfl.import_draft_picks(years)
```
Returns list of draft picks for the years specified

years
: optional, list of years to pull

```python
nfl.import_draft_values()
```
Returns relative values by generic draft pick according to various popular valuation methods

```python
nfl.import_team_desc()
```
Returns dataframe with color/logo/etc information for all NFL team

```python
nfl.import_schedules(years)
```
Returns dataframe with schedule information for years specified

years
: required, list of years to pull data for (earliest available is 1999)

```python
nfl.import_combine_data(years, positions)
```
Returns dataframe with combine results for years and positions specified

years
: optional, list or range of years to pull data from

positions
: optional, list of positions to be pulled (standard format - WR/QB/RB/etc.)

```python
nfl.import_ids(columns, ids)
```
Returns dataframe with mapped ids for all players across most major NFL and fantasy football data platforms

columns
: optional, list of columns to return

ids
: optional, list of ids to return

```python
nfl.import_ngs_data(stat_type, years)
```
Returns dataframe with specified NGS data

columns
: required, type of data (passing, rushing, receiving)

years
: optional, list of years to return data for

```python
nfl.import_depth_charts(years)
```
Returns dataframe with depth chart data

years
: optional, list of years to return data for

```python
nfl.import_injuries(years)
```
Returns dataframe of injury reports

years
: optional, list of years to return data for

```python
nfl.import_qbr(years, level, frequency)
```
Returns dataframe with QBR history

years
: optional, years to return data for

level
: optional, competition level to return data for, nfl or college, default nfl

frequency
: optional, frequency to return data for, weekly or season, default season

```python
nfl.import_pfr(s_type, years)
```
Returns dataframe of data sourced from https://www.pro-football-reference.com/

s_type (str)
: required, the type of stat data to request. Must be one of pass, rec, or rush.

years (List[int])
: optional, years to return data for

```python
nfl.import_snap_counts(years)
```
Returns dataframe with snap count records

years
: optional, list of years to return data for

**Additional features**
```python
nfl.cache_pbp(years, downcast=True, alt_path=None)
```
Caches play-by-play data locally to speed up download time. If years specified have already been cached they will be overwritten, so if using in-season must cache 1x per week to catch most recent data

years
: required, list or range of years to cache

downcast
: optional, converts float64 columns to float32, reducing memory usage by ~30%. Will slow down initial load speed ~50%

alt_path
:optional, alternate path to store pbp cache - default is in program created user Local folder

```python
nfl.clean_nfl_data(df)
```
Runs descriptive data (team name, player name, etc.) through various cleaning processes

df
: required, dataframe to be cleaned

## Recognition
I'd like to recognize all of [Ben Baldwin](https://twitter.com/benbbaldwin), [Sebastian Carl](https://twitter.com/mrcaseb), and [Lee Sharpe](https://twitter.com/LeeSharpeNFL) for making this data freely available and easy to access. I'd also like to thank [Tan Ho](https://twitter.com/_TanH), who has been an invaluable resource as I've worked through this project, and Josh Kazan for the resources and assistance he's provided.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
