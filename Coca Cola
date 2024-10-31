import streamlit as st
import yfinance as yf
import datetime

# Specify title and logo for the webpage.
# Set up your web app
st.set_page_config(layout="wide", page_title="Coca-Cola Stock Price")

# Display title
st.title("Coca-Cola Stock Price")

# Define the stock symbol
symbol = "KO"

# Get stock data
try:
    stock = yf.Ticker(symbol)
    # Get historical market data
    end_date = datetime.date.today()
    start_date = end_date - datetime.timedelta(days=365) # get data from last 1 year

    data = yf.download(symbol, start=start_date, end=end_date)


    if data.empty:
        st.error("No data found for the given timeframe.")
    else:
        # Display opening and closing prices
        st.write(f"**Opening Price (Latest):** ${data['Open'][-1]:.2f}")
        st.write(f"**Closing Price (Latest):** ${data['Close'][-1]:.2f}")
        st.write(f"**Symbol:** {symbol}")

        # Display chart
        st.line_chart(data['Close'])

except Exception as e:
    st.error(f"An error occurred: {e}")
