# Gym Tinder

A notebook that matches gym members with compatible training partners. Each member's profile (age, training frequency, training type, preferred time and days, fitness level, goal, social preference, experience and tenure) is turned into a numeric vector. Categorical fields are label-encoded, the preferred training hour is encoded on a circle as sine and cosine so that 23:00 sits close to 06:00, and the financial fields are left out. The vectors are standardised and matches are ranked by Euclidean distance, with an optional filter on sex. The notebook runs this on a synthetic member dataset and returns the five closest matches for a target member, along with plots of the member distributions and the match distances.

The approach is written up in the Medium article [Building the Tinder Algorithm for Gyms: A Data Science Love Story](https://medium.com/@karl.foster/building-the-tinder-algorithm-for-gyms-a-data-science-love-story-2e96dbaaee39) (24 July 2025).

## What is in the repository

- `match_maker.ipynb`: the notebook. It loads the dataset, inserts a target profile in place of the first row, explores the data, encodes and scales the features, computes the distance matrix, prints a comparison table of the top matches and plots the results.
- `synthetic_gym_members_dataset.csv`: a synthetic dataset of 10,000 gym members. The data is generated, not real. It has 18 columns: `member_id`, `name`, `age`, `sex`, `training_frequency_per_week`, `training_type`, `preferred_time_slot`, `preferred_hour`, `preferred_days`, `schedule_preference`, `tenure_months`, `freeze_period`, `lifetime_value`, `fitness_level`, `primary_goal`, `social_preference`, `experience_level` and `monthly_value`.

## Running it

The notebook was written against Python 3.13 and imports `pandas`, `numpy`, `matplotlib`, `seaborn` and `scikit-learn`.

```sh
pip install jupyter pandas numpy matplotlib seaborn scikit-learn
jupyter notebook match_maker.ipynb
```

Run the cells in order. The notebook expects `synthetic_gym_members_dataset.csv` in the same directory. To match a different member, change `my_profile` in the first code cell under "Loading and exploring the data", or change `target_member_id`, `gender_filter` and `num_matches` in the call to `find_compatible_matches`.

## Licence

MIT. See [LICENSE](LICENSE).
