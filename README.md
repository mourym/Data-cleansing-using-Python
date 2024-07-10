import pandas as pd
df = pd.read_excel(r"C:\Users\mourym\Downloads\Customer Call List.xlsx")

df
df = df.drop_duplicates()
df

df = df.drop(columns="Not_Useful_Column")
df

# df["Last_Name"] = df["Last_Name"].str.lstrip("/")
# df["Last_Name"] = df["Last_Name"].str.lstrip(".")
df["Last_Name"] = df["Last_Name"].str.strip("123./_")
df
df["Phone_Number"] = df["Phone_Number"].str.replace('[^a-zA-Z0-9]','')
df

# df['Phone_Number'].apply(lambda x: x[0:3] + '-' + x[3:6] + '-' + x[6:10])

# df['Phone_Number'] = df['Phone_Number'].apply(lambda x:str(x))
# df['Phone_Number'] = df['Phone_Number'].apply(lambda x: x[0:3] + '-' + x[3:6] + '-' + x[6:10])

df['Phone_Number'] = df['Phone_Number'].str.replace('nan--','')
df['Phone_Number'] = df['Phone_Number'].str.replace('Na--','')
df



df[["Street_Address","State","Zip_code"]]=df["Address"].str.split(",",2,expand =True)
dfdf['Do_Not_Contact'] = df['Do_Not_Contact'].replace('No','N')
df['Do_Not_Contact'] = df['Do_Not_Contact'].replace('Yes','Y')
df




df = df.replace('N/a','')
df = df.fillna('')


for x in df.index:
    if df.loc[x,"Do_Not_Contact"]=='Y':
        df.drop(x,inplace=True)

dffor x in df.index:
    if df.loc[x,"Phone_Number"]=='':
        df.drop(x,inplace=True)
        
#another way to drop null values
# df = df.dropna(subset="Phone_Number",inplace=True)


# df = df.reset_index(drop=True)
df
