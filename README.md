import json, requests

base_url = "https://api.openweathermap.org/data/2.5/weather"
appid = "99dd3a9554dc4d210b5d1c2f0ddd0fed"
location=""
url = f"{base_url}?q={location}&units=imperial&APPID={appid}"
print(url)
print()
response = requests.get(url)
unformated_data = response.json() 

# "404", means city is found otherwise,
# city is not found

print = input("Enter your desired location using city, state or zip code: ")
if unformated_data["cod"] != "404":
  #print (unformatted_data)
    # store the value of "main"
    # key in variable y
   y = unformated_data["main"]
   current_temp = y["temp"]
   current_tempmax= y["temp_max"]
else:
   print(" City Not Found ")
  #print(unformated_data)

   temp = unformated_data["main"]["temp"]
   print(f"The current temp is: {temp}")
   temp_max = unformated_data["main"]["temp_max"]
   print(f"The max temp is: {temp_max}")
 

#prompt user to continue or end session

repeat = int(input("Would you like to enter a new location? Yes(1) or No(2): "))
#if user selects option 1 (yes) then 
    
if repeat == 1:
  print("Enter new desired location: ")
  #if user select option 2 (no) then
elif repeat == 2:
  print("Have a nice day!")
  #if user selects other than
  
else:
  print("You did not choose a valid option")
