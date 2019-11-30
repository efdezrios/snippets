# Altair code
```python
import altair as alt
```

## Histogram

```python
alt.Chart(brain_body).mark_bar().encode(
    x=alt.X('Brain Weight',bin=alt.Bin(maxbins=20)),
    y='count()'
)
```

## Barra
```python
alt.Chart(trends).mark_bar().encode(
    y='mean(value)',
    x='search_term',
    color='search_term'
).properties(
    width=250
)
```

## Line
```python
alt.Chart(trends).mark_line().encode(
    x=alt.X('date:T', timeUnit='year'),
    y='mean(value)',
    color='search_term'
)
```

## Scatter
```python
alt.Chart(brain_body).mark_circle().encode(
    x='Brain Weight',
    y='Body Weight'
).properties(
    width=860
)

alt.Chart(brain_body).mark_`point().encode(
    x='Brain Weight',
    y='Body Weight'
).properties(
    width=860
)
```

## Concatenation
```python
|
```

## Selection single
```python
select_term=alt.selection_single(encodings=['x'])

trend_line=alt.Chart(trends).mark_line().encode(
    x=alt.X('date:T', timeUnit='year'),
    y='mean(value)',
    color='search_term'
).transform_filter(select_term)

trend_bar=alt.Chart(trends).mark_bar().encode(
    y='mean(value)',
    x='search_term',
    color='search_term'
).properties(
    width=250,
    selection=select_term
)

(trend_bar|trend_line).properties(
    title='Google trends'
).save('selector.html')
```

## Selection double
```python
select_zoom=alt.selection_interval(encodings=['x'])

trend_line=alt.Chart(trends).mark_line().encode(
    x=alt.X('date:T', timeUnit='year'),
    y='mean(value)',
    color='search_term'
).transform_filter(
    select_zoom
)

trend_line2=alt.Chart(trends).mark_line().encode(
    x=alt.X('date:T', timeUnit='year'),
    y='mean(value)',
    color='search_term'
).properties(
    height=100,
    selection=select_zoom
)

(trend_line&trend_line2).properties(
    title='Google trends'
).save('zoom.html')
```
