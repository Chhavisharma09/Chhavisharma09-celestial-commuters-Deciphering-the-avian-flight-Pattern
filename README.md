# Chhavisharma09-celestial-commuters-Deciphering-the-avian-flight-Pattern

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

load data
# cleaning data

df=df.drop(["Unnamed: 0"],axis=1)

df.info()
df.isnull().sum()
df_cleaned=df.dropna()
df_cleaned=df.dropna(subset=['direction'])
df_cleaned=df.dropna(axis=1)
df_cleaned=df.dropna(axis=1)
df.dropna(inplace=True)
df.isnull().sum()

df.describe()
df.drop_duplicates(inplace=True)
duplicate_rows=df[df.duplicated()]
df.dropna(inplace=True)
df["altitude"].fillna(df['altitude'].mean(),inplace=True)

 # Exploratory data analysis


 print(df.info())
 print(df.describe())
 
 # Histograms
 df[['altitude','speed_2d','latitude','longitude']].hist(figsize=(10,8))
plt.show()

# Bar chart
sns.countplot(x="bird_name",data=df)
plt.show()
sns.countplot(x='direction', data=df)
plt.show()
sns.scatterplot(x='altitude',y='speed_2d', data=df)
plt.show()
# Time series plot
plt.figure(figsize=(10, 6))
plt.plot(df['date_time'], df['bird_name'], marker='o', linestyle='-')
plt.xlabel('date_time')
plt.ylabel('bird_name')
plt.title('Bird Sightings Over Time')
plt.xticks(rotation=45)
plt.show()
print(df.isnull().sum())
sns.boxplot(x='direction',y='speed_2d', data=df)
plt.show()
sns.boxplot(x='altitude', data=df)
plt.show()

bird_counts = df['bird_name'].value_counts()

print(bird_counts)

india_birds_df = df[df['destination'] == 'India']

# Count occurrences of each bird name in India
india_bird_counts = india_birds_df['bird_name'].value_counts()

print(india_bird_counts)

df['date_time'] = pd.to_datetime(df['date_time'])

# Extract month from the 'date_time' column
df['month'] = df['date_time'].dt.month

# Define a function to map months to seasons
def get_season(month):
    if month in [3, 4, 5]:
        return 'Spring'
    elif month in [6, 7, 8]:
        return 'Summer'
    elif month in [9, 10, 11]:
        return 'Autumn'
    else:
        return 'Winter'

# Apply the function to create a new column 'season'
df['season'] = df['month'].apply(get_season)

# Count occurrences of each season
season_counts = df['season'].value_counts()

print(season_counts)
india_lat_range = (8, 38)
india_lon_range = (68, 98)

# Filter rows where latitude and longitude fall within India's range
india_birds_df = df[(df['latitude'].between(*india_lat_range)) & (df['longitude'].between(*india_lon_range))]

# Count occurrences of each bird name in the filtered DataFrame
india_bird_counts = india_birds_df['bird_name'].value_counts()

print(india_bird_counts)
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# Assuming the columns 'Bird name', 'date_time', 'latitude', and 'longitude' exist in your DataFrame

# Plot migration paths for each bird species
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='longitude', y='latitude', hue='bird_name', palette='tab10', legend='full')
plt.title('Migration Paths of Different Bird Species')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.legend(bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# Assuming the columns 'Bird name', 'date_time', 'latitude', and 'longitude' exist in your DataFrame

# Plot migration paths for each bird species
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='longitude', y='latitude', hue='bird_name', palette='tab10', legend='full')
plt.title('Migration Paths of Different Bird Species')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.legend(bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()













 
