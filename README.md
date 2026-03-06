# Weighty

This is a Vibe Coded Weight Loss Tracker App

## What it does

- Imports your starting profile from the workbook
- Imports weekly weigh-ins and daily calorie/weight entries from the workbook
- Recreates the core workbook math for:
  - BMI
  - BMR
  - TDEE estimates
  - Weekly calorie deficit
  - Estimated fat loss based on a 3,500 calorie pound-of-fat rule
- Gives you a browser dashboard, daily entry page, weekly check-in page, and profile editor
- Runs on port **1055**

## Run it

```bash
docker compose up -d --build
```

Then browse to:

```text
http://localhost:1055
```

## Notes

- Data is stored in `./data/tracker.db`
- The workbook is imported automatically on first launch if the file is mounted in the expected location
- You can re-import the workbook from the dashboard later
- The current build focuses on the workbook's calculation flow, not every single spreadsheet cell or visual exactly 1:1

## Formula mapping from the workbook

- **BMI** = `703 * weight / height^2`
- **BMR** = `4.38*weight + 14.55*height - 5.08*age + 260`
- **TDEE** = `BMR * activity_multiplier`
- **Estimated fat loss** = `weekly_deficit / 3500`

