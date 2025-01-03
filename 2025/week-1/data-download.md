## Download instructions:
- Go to Joe Hovde's [google sheet](https://docs.google.com/spreadsheets/d/1O_zxndHKhKMIfJ9e7_M5L7b4F3S__d1nVnUS8iZn8yE/edit?gid=0#gid=0) and download it as a CSV sheet. Click File --> Download --> Comma Separate Values
- Save the CSV sheet in the same directory as the file of Python code provided below, and run code.

```python
import plotly.express as px
import pandas as pd

df = pd.read_csv('NYC Marathon Results, 2024 - Marathon Runner Results.csv')

# Convert `pace` column from string format (minutes:seconds) to numeric (float) in minutes
def convert_pace_to_minutes(pace_str):
    try:
        minutes, seconds = map(int, pace_str.split(':'))
        return minutes + seconds / 60
    except ValueError:
        return None

# Apply conversion to the `pace` column
df['pace_minutes'] = df['pace'].apply(convert_pace_to_minutes)

# Drop rows where `pace_minutes` could not be calculated
cleaned_data = df.dropna(subset=['pace_minutes'])

# Define age groups
bins = [10, 20, 30, 40, 50, 60, 70, 80, 90]
labels = ['10-20', '20-30', '30-40', '40-50', '50-60', '60-70', '70-80', '80-90']

# Create a new column for age groups
cleaned_data['age_group'] = pd.cut(cleaned_data['age'], bins=bins, labels=labels, right=False)

fig = px.violin(
    cleaned_data,
    x='age_group',
    y='pace_minutes',
    title='Distribution of Minutes per Mile, by Age Group',
    labels={'pace_minutes': 'Pace (minutes per mile)', 'age': 'Age'},
    box=True
)
fig.update_xaxes(categoryorder='array', categoryarray=labels)

fig.show()
```
