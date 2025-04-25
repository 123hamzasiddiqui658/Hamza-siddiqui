# Hamza-siddiqui

from datetime import datetime

def is_valid_date(date_str):
    if len(date_str) != 10:
        print("❌ Date must be in DD-MM-YYYY format.")
    elif date_str[2] != '-' or date_str[5] != '-':
        print("❌ Use hyphens (-) in the correct positions.")
    else:
        day, month, year = date_str.split('-')
        if not (day.isdigit() and month.isdigit() and year.isdigit()):
            print("❌ Date must contain only numbers.")
        else:
            day = int(day)
            month = int(month)
            year = int(year)
            today = datetime.today()

            if day < 1 or day > 31:
                print("❌ Day must be between 1 and 31.")
            elif month < 1 or month > 12:
                print("❌ Month must be between 1 and 12.")
            elif year > today.year:
                print("❌ Year cannot be in the future.")
            else:
                # Age calculation
                birthdate = datetime.strptime(date_str, "%d-%m-%Y")
                age_years = today.year - birthdate.year
                age_months = today.month - birthdate.month
                age_days = today.day - birthdate.day

                if age_days < 0:
                    age_months -= 1
                    age_days += 30  # approx

                if age_months < 0:
                    age_years -= 1
                    age_months += 12

                print("✅ Age Calculation Result:")
                print("You are", age_years, "years,", age_months, "months and", age_days, "days old.")
                return  # Remove this line if your sir hasn't allowed even this

    print("⚠️ Please try again with correct date.")

# User Input
print("📅 Please enter your Date of Birth in DD-MM-YYYY format.")
dob_input = input("Enter your Date of Birth (DD-MM-YYYY): ")
is_valid_date(dob_input)
