import pandas as pd
import matplotlib.pyplot as plt

# Create data directly (NO CSV needed)
data = {
    "Roll": [1, 2, 3, 4, 5],
    "Name": ["Asha", "Ravi", "Neha", "Aman", "Pooja"],
    "Maths": [78, 45, 90, 60, 30],
    "Science": [85, 50, 88, 65, 40],
    "English": [74, 48, 92, 70, 35]
}

df = pd.DataFrame(data)

# Calculations
df["Total"] = df[["Maths", "Science", "English"]].sum(axis=1)
df["Average"] = df["Total"] / 3
df["Result"] = df["Average"].apply(lambda x: "Pass" if x >= 40 else "Fail")

# Display table
print(df)

# Topper
print("Topper:", df.loc[df["Total"].idxmax(), "Name"])

# Graph 1: Total Marks
plt.figure()
plt.bar(df["Name"], df["Total"])
plt.title("Total Marks of Students")
plt.xlabel("Students")
plt.ylabel("Total Marks")
plt.show()

# Graph 2: Pass vs Fail
result_count = df["Result"].value_counts()
plt.figure()
plt.pie(result_count, labels=result_count.index, autopct="%1.1f%%")
plt.title("Pass vs Fail Percentage")
plt.show()


