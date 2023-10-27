Create by binoy 
# #Phone number find location.

Today I’m going to share with you how to build a simple desktop application to identify and track country information from phone numbers.

It’s a very basic app, therefore you just need to have the basics of Python to be able to complete this tutorial.



## requirements

- phone-iso3166
- pycountry
- Tkinter
Please install the above python libraries for you to able to completely follow through this Tutorial

TESTED ON ALL OPERATIVE SYSTEM 

-   Kali Linux
- Termux
- MacOS
 - Ubuntu
- Parrot Sec OS
## Installation
install in linux 
```bash
 sudo apt install python3 
```
```bash
 pip  install python-tk, phone-iso3166 , pycountry
```
 We are going to use phone-iso3166 to determine the get alpha_2 letters of the country from the number and pycountry to determine the official name of the country using alpha_2 letters we obtained from phone-iso3166.   

app.py
 ```bash
 import json 
import pycountry
from tkinter import Tk, Label, Button, Entry
from phone_iso3166.country import phone_country


class Location_Tracker:
    def __init__(self, App):
        self.window = App
        self.window.title("Phone number Tracker")
        self.window.geometry("500x400")
        self.window.configure(bg="#3f5efb")
        self.window.resizable(False, False)

       
        Label(App, text="Enter a phone number",fg="white", font=("Times", 20), bg="#3f5efb").place(x=150,y= 30)
        self.phone_number = Entry(App, width=16, font=("Arial", 15), relief="flat")
        self.track_button = Button(App, text="Track Country", bg="#22c1c3", relief="sunken")
        self.country_label = Label(App,fg="white", font=("Times", 20), bg="#3f5efb")

        self.phone_number.place(x=170, y=120)
        self.track_button.place(x=200, y=200)
        self.country_label.place(x=100, y=280)

        self.track_button.bind("<Button-1>", self.Track_location)
        
    def Track_location(self,event):
        phone_number = self.phone_number.get()
        country = "Country is Unknown"
        if phone_number:
            tracked = pycountry.countries.get(alpha_2=phone_country(phone_number))
            print(tracked)
            if tracked:
                country = tracked.official_name
        self.country_label.configure(text=country)

PhoneTracker = Tk()
MyApp = Location_Tracker(PhoneTracker)
PhoneTracker.mainloop()
```

## Screenshots

![App Screenshot](https://firebasestorage.googleapis.com/v0/b/hackernoon-app.appspot.com/o/images%2FMJpFVUEItkSdoh38rYo60VT7RfH3-4w1j4wtq.jpeg?alt=media&token=3cd55dc1-ed6a-41f7-b435-451515ec4679)

