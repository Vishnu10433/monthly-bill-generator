
        

# Provided item list
item_list = [
    {"idx": 1, "item_code": "Executive Desk (4*2)", "sales_description": "Dedicated Executive Desk", "qty": 10, "rate": "1000", "amount": "10000", "start_date": "2023-11-01", "stop_date": "2024-10-17"},
    {"idx": 2, "item_code": "Executive Desk (4*2)", "qty": "10", "rate": "1080", "amount": "10800", "start_date": "2024-10-18", "stop_date": "2025-10-31"},
    {"idx": 3, "item_code": "Executive Desk (4*2)", "qty": 15, "rate": "1080", "amount": "16200", "start_date": "2024-11-01", "stop_date": "2025-10-31"},
    {"idx": 4, "item_code": "Executive Desk (4*2)", "qty": 5, "rate": "1000", "amount": "5000", "start_date": "2024-11-01", "stop_date": "2025-10-31"},
    {"idx": 5, "item_code": "Manager Cabin", "qty": 5, "rate": 5000, "amount": 25000, "start_date": "2024-11-01", "stop_date": "2025-10-31"},
    {"idx": 6, "item_code": "Manager Cabin", "qty": 7, "rate": "5000", "amount": 35000, "start_date": "2024-12-15", "stop_date": "2025-10-31"},
    {"idx": 7, "item_code": "Manager Cabin", "qty": 10, "rate": 4600, "amount": 46000, "start_date": "2023-11-01", "stop_date": "2024-10-17"},
    {"idx": 8, "item_code": "Parking (2S)", "qty": 10, "rate": 1000, "amount": 10000, "start_date": "2024-11-01", "stop_date": "2025-10-31"},
    {"idx": 9, "item_code": "Parking (2S)", "qty": 10, "rate": 0, "amount": 0, "start_date": "2024-11-01", "stop_date": "2025-10-31"},
    {"idx": 10, "item_code": "Executive Desk (4*2)", "qty": "8", "rate": "1100", "amount": "8800", "start_date": "2024-11-15", "stop_date": "2025-01-31"},
    {"idx": 11, "item_code": "Manager Cabin", "qty": "3", "rate": "5200", "amount": "15600", "start_date": "2024-10-10", "stop_date": "2024-11-10"},
    {"idx": 12, "item_code": "Conference Table", "qty": 1, "rate": "20000", "amount": "20000", "start_date": "2024-11-05", "stop_date": "2024-11-20"},
    {"idx": 13, "item_code": "Parking (2S)", "qty": 5, "rate": "1000", "amount": "5000", "start_date": "2024-11-15", "stop_date": "2025-02-28"},
    {"idx": 14, "item_code": "Reception Desk", "qty": 2, "rate": "7000", "amount": "14000", "start_date": "2024-11-01", "stop_date": "2025-03-31"},
    {"idx": 15, "item_code": "Reception Desk", "qty": 1, "rate": "7000", "amount": "7000", "start_date": "2024-11-10", "stop_date": "2024-11-25"},
    {"idx": 16, "item_code": "Breakout Area", "qty": 3, "rate": "3000", "amount": "9000", "start_date": "2024-01-01", "stop_date": "2024-01-31"}
]

# Run function for November 2024
generate_monthly_bill(item_list, "2024-11")

