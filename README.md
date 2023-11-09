import pandas as pd

# Создание фрейма данных для Fashion_Retail_Sales
sales_data = {
    'Customer Reference ID': [4018, 4115, 4019, 4097, 3997, 4080, 4055, 3973, 4044, 4010, 4108, 4067, 4068, 4102, 4044, 4096, 4017],
    'Item Purchased': ['Handbag', 'Tunic', 'Tank Top', 'Leggings', 'Wallet', 'Onesie', 'Jacket', 'Trousers', 'Jeans', 'Loafers', 'Slippers', 'Bowtie', 'Pajamas', 'Trench Coat', 'Handbag', 'Poncho', 'Gloves'],
    'Purchase Amount (USD)': [4619.0, 2456.0, 2102.0, 3126.0, 3003.0, 2914.0, 2571.0, 2419.0, 4771.0, 4233.0, 2356.0, 4418.0, 3728.0, 2130.0, 2122.0, 2383.0, 2895.0],
    'Date Purchase': ['2023-02-05', '2023-07-11', '2023-03-23', '2023-03-15', '2022-11-27', '2022-12-11', '2023-07-08', '2022-11-10', '2023-05-19', '2023-06-11', '2023-03-19', '2022-11-21', '2022-12-09', '2023-01-29', '2023-08-01', '2023-04-10', '2023-07-17'],
    'Review Rating': [None, 2.0, 4.1, 3.2, 4.7, 4.5, 1.3, 4.6, 4.1, None, 4.8, 3.4, None, 4.8, 1.2, None, 3.6],
    'Payment Method': ['Credit Card', 'Credit Card', 'Cash', 'Cash', 'Cash', 'Credit Card', 'Cash', 'Cash', 'Cash', 'Credit Card', 'Credit Card', 'Cash', 'Credit Card', 'Cash', 'Credit Card', 'Credit Card', 'Credit Card']
}

fashion_sales_frame = pd.DataFrame(sales_data)

def средний_чек(df): 
    """Вычисляет среднюю сумму покупки."""
    return df['Purchase Amount (USD)'].mean()

def количество_продаж(df):
    """Возвращает общее количество продаж."""
    return len(df)

def топ_клиенты(df, n=3):
    """Возвращает топ n клиентов по суммарной сумме покупок."""
    top_customers = df.groupby('Customer Reference ID')['Purchase Amount (USD)'].sum().sort_values(ascending=False).head(n)
    return top_customers

# Пример использования функций
средний_чек_покупки = средний_чек(fashion_sales_frame)
print(f"Средний чек покупки: {средний_чек_покупки}")

количество_продаж = количество_продаж(fashion_sales_frame)
print(f"Общее количество продаж: {количество_продаж}")

топ_клиентов = топ_клиенты(fashion_sales_frame)
print("Топ клиентов по суммарной сумме покупок:")
print(топ_клиентов)
