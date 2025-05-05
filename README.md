from datetime import datetime, timedelta
from collections import defaultdict

def generate_monthly_bill(item_list: list, target_month: str) -> dict:
    # Parse target month start and end
    month_start = datetime.strptime(target_month + "-01", "%Y-%m-%d")
    next_month = (month_start.replace(day=28) + timedelta(days=4)).replace(day=1)
    month_end = next_month - timedelta(days=1)
    total_days_in_month = (month_end - month_start).days + 1

    groups = defaultdict(lambda: {"qty": 0, "amount": 0.0})
    
    for item in item_list:
        # Parse dates
        start = datetime.strptime(item["start_date"], "%Y-%m-%d")
        stop = datetime.strptime(item["stop_date"], "%Y-%m-%d")
        
        # Calculate overlap with the target month
        active_start = max(start, month_start)
        active_end = min(stop, month_end)
        active_days = (active_end - active_start).days + 1
        
        if active_days <= 0:
            continue  # Not active in target month

        # Parse and clean values
        rate = float(item["rate"])
        qty = int(item["qty"])
        
        # Daily rate per unit
        daily_rate_per_unit = rate / total_days_in_month
        amount = round(qty * daily_rate_per_unit * active_days, 2)

        billing_period = f"{active_start.date()} to {active_end.date()}"
        key = (item["item_code"], rate, billing_period)
        
        groups[key]["qty"] += qty
        groups[key]["amount"] += amount

    # Format output
    line_items = []
    total_revenue = 0.0

    for (item_code, rate, billing_period), data in groups.items():
        line_item = {
            "item_code": item_code,
            "rate": rate,
            "qty": data["qty"],
            "amount": round(data["amount"], 2),
            "billing_period": billing_period
        }
        total_revenue += data["amount"]
        line_items.append(line_item)

    return {
        "line_items": line_items,
        "total_revenue": round(total_revenue, 2)
    }

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

