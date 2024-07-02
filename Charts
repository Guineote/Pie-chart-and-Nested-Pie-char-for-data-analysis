import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

file_path = 'HAM10000_metadata.csv'
df = pd.read_csv(file_path)
def nested_pie_chart(inner_data, outer_data, inner_labels, outer_labels, inner_colors, outer_colors, title):
    fig, ax = plt.subplots()
    size = 0.3
    
    # Inner pie
    ax.pie(inner_data, radius=1-size, labels=inner_labels, autopct='%1.1f%%', colors=inner_colors, wedgeprops=dict(width=size, edgecolor='w'))
    
    # Outer pie
    ax.pie(outer_data, radius=1, labels=outer_labels, autopct='%1.1f%%', colors=outer_colors, wedgeprops=dict(width=size, edgecolor='w'))
    
    plt.title(title)
    plt.show()

# Datos para age y sex
age_bins = pd.cut(df['age'], bins=[0, 18, 35, 50, 65, 80, 100], right=False)
age_values = age_bins.value_counts().values
age_labels = age_bins.value_counts().index
sex_counts = df['sex'].value_counts()
sex_colors = {'male': 'lightblue', 'female': 'lightpink', 'unknown': 'lightgray'}
outer_colors_age_sex = [sex_colors[sex] for sex in sex_counts.index]
inner_colors_age_sex = plt.cm.Paired(np.linspace(0, 1, len(age_values)))

# Datos para dx y dx_type
dx_counts = df['dx'].value_counts()
dx_type_counts = df['dx_type'].value_counts()
dx_colors = {
    'akiec': 'lightcoral', 'bcc': 'lightgreen', 'bkl': 'lightblue', 'df': 'lightgoldenrodyellow',
    'mel': 'lightpink', 'nv': 'lightsalmon', 'vasc': 'lightgray'
}
outer_colors_dx_dxtype = [dx_colors[dx] for dx in dx_counts.index]
inner_colors_dx_dxtype = plt.cm.Paired(np.linspace(0, 1, len(dx_counts)))
nested_pie_chart(age_values, sex_counts.values, age_labels, sex_counts.index, inner_colors_age_sex, outer_colors_age_sex, 'Age and Sex')
nested_pie_chart(dx_counts.values, dx_type_counts.values, dx_counts.index, dx_type_counts.index, inner_colors_dx_dxtype, outer_colors_dx_dxtype, 'Diagnosis (dx) and Diagnosis Type (dx_type)')
localization_values = df['localization'].value_counts().values
localization_labels = df['localization'].value_counts().index
colors = plt.get_cmap('tab20')(np.linspace(0, 1, len(localization_values)))

plt.figure(figsize=(8, 8))
plt.pie(localization_values, labels=localization_labels, autopct='%1.1f%%', startangle=140, colors=colors)
plt.title("Localization")
plt.axis('equal')
plt.show()
