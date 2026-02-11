import streamlit as st
import pandas as pd
import numpy as np

st.set_page_config(page_title="My Dashboard", layout="wide")

st.title("📊 My First Streamlit Dashboard")

st.sidebar.header("Filters")

# Sample data
data = pd.DataFrame({
    "Year": np.arange(2015, 2025),
    "Accidents": np.random.randint(1000, 5000, 10),
    "Fatalities": np.random.randint(200, 1000, 10)
})

year = st.sidebar.selectbox("Select Year", data["Year"])

filtered = data[data["Year"] == year]

col1, col2 = st.columns(2)

col1.metric("Accidents", int(filtered["Accidents"]))
col2.metric("Fatalities", int(filtered["Fatalities"]))

st.line_chart(data.set_index("Year"))
