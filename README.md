# Do Comics Mirror America?

**Women at work in Marvel and DC characters vs. the real U.S. workforce, 1940 to 2025**

Final team project (Team A07) for an Intro to Data Analysis class. The whole project lives in one Jupyter notebook: [`Final-A07-Do-Comics-Mirror-America.ipynb`](Final-A07-Do-Comics-Mirror-America.ipynb).

**Team:** Daniel Igbokwe, Carly Barry, Eliza Bashirian, Albert Dorofeev, Emanuele Borroni (Project Manager: Albert Dorofeev)

## The question

Since the 1940s, American women have moved into paid work and into jobs once open only to men. Did Marvel and DC comics reflect that change, lead it, or lag behind it? We compare the jobs comic book characters hold with the jobs real American women held at the same time, written for an editorial team deciding how to create and cast new characters.

## Data

| Dataset | Source | Size (raw) |
|---|---|---|
| Marvel characters | [Marvel Database](https://marvel.fandom.com/wiki/Category:Earth-616/Characters) (Fandom wiki), scraped | 37,204 rows |
| DC characters | [DC Database](https://dc.fandom.com/wiki/DC_Comics_Database) (Fandom wiki), scraped | 14,671 rows |
| U.S. jobs by sex, 1940 to 2023 | [IPUMS USA](https://usa.ipums.org/usa/) (Census and ACS) | 5,772 rows |
| Women's labor force participation, 1948 to 2026 | [BLS via FRED](https://fred.stlouisfed.org/series/LNS11300002) | 944 rows |

The raw CSV files are **not** included in this repo (IPUMS data may not be redistributed). The notebook was built to run in Google Colab with the data in a Google Drive folder.

## What the notebook does

1. **Data cleaning.** Grouped 83 messy gender values into Male / Female / Other / Unknown, stripped wiki markup, and sorted about 15,000 free-text occupations into census job groups (plus comic-only groups like Criminal, Hero and Royalty/Mystic). Removed 1,953 duplicate DC characters caused by reboots, leaving **49,922 characters**.
2. **Joins.** Linked characters to real U.S. jobs by job group and decade, and linked the yearly female share of new characters to women's labor force participation by year.
3. **Analysis.** 16 questions in four sections, each with a hypothesis, a chart, an answer, an interpretation and a caveat:
   - **A. Baseline:** gender split, debut years, and how the female share of new characters changed by decade (Q1 to Q4)
   - **B. Lag:** does comics track the workforce, and how many years behind? (Q5 to Q8)
   - **C. Jobs:** what jobs female characters get compared with real women (Q9 to Q14)
   - **D. Working lives:** are female characters given an occupation at all? (Q15, Q16)

## Key findings

- **Comics lag about 7 years behind.** The female share of new characters moves with women's labor force participation (r = 0.83) and lines up best with the workforce of about 7 years earlier (r = 0.89). This is a correlation, not proof that comics react to society.
- **The roster is still about 70% male, but new characters changed fast.** Women went from 11.5% of new characters in 1960 to 40.0% in 2025.
- **Female characters get "women's jobs".** Their job groups are on average 50.1% female in the real workforce, vs 42.9% for male characters. In historically male jobs, female characters reached 20% only in the 2010s; real women did in the 1980s.
- **Women are written with fewer working lives.** 57.1% of female characters have an occupation listed, vs 66.7% of male characters.

## Tools

Python, pandas, NumPy, Matplotlib and seaborn, run in Google Colab.

## How to run it

1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Put the four raw CSV files in a Google Drive folder (the notebook looks for the `000-Project/Datasets` folder).
3. Run all cells. Colab will ask for permission to mount your Google Drive.

If you just want to read the results, open the notebook on GitHub: all charts and outputs are already saved in it.

## Limitations

- Wiki data is written by volunteers, so some genders and occupations are missing or incomplete.
- Only about a fifth of characters hold a job that matches a census job group, and the groups are broad.
- The 2020s are an unfinished decade, and the earliest decades rest on few characters.
- Correlation over time does not show that the workforce caused the change in comics.

The notebook also includes a full data dictionary, the challenges we ran into, recommendations, references, and a Generative AI disclosure.
