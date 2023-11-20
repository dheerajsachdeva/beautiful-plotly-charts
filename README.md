In this lesson we looked at how to:

Pull a random sample from a DataFrame using .sample()

How to find duplicate entries with .duplicated() and .drop_duplicates()

How to convert string and object data types into numbers with .to_numeric()

How to use plotly to generate beautiful pie, donut, and bar charts as well as box and scatter plots

**Solution: Working with Nested Column Data**

If we look at the number of unique values in the Genres column we get 114. But this is not accurate if we have nested data like we do here. We can see this using .value_counts() and looking at the values that just have a single entry. There we see that the semi-colon (;) separates the genre names.

We somehow need to separate the genre names to get a clear picture. This is where the string’s .split() method comes in handy. After we’ve separated our genre names based on the semi-colon, we can add them all into a single column with .stack() and then use .value_counts().



# Split the strings on the semi-colon and then .stack them.
stack = df_apps_clean.Genres.str.split(';', expand=True).stack()
print(f'We now have a single column with shape: {stack.shape}')
num_genres = stack.value_counts()


