# kivy framework imports
from kivy.app import App
from kivy.uix.widget import Widget
from kivy.properties import ObjectProperty
from kivy.uix.screenmanager import *
from kivy.clock import Clock
from kivy.core.audio import SoundLoader

# import hyperlink
import webbrowser

# import random
from random import *

# import system time
import time

# make a list out of the fortune cookie quotes
cookiequotes = ["Things could be worse, {}", "Look, {}, it cannot always be\n this great",
                 "Hey {}, your unlucky numbers are:\n 13, 9, 666, 69", "Be patient, {}, there are \neven darker days ahead!",
                 "At least your country is not at war, {}!", "change is just around the corner, {}. \nBut is it for the better?",
                  "Everything's fine, {}?\nIt won't last!", "No lucky numbers for you {}!"]

# make list out of fortune cookie image directories
cookiedirs = ["./assets/cookie1.png", "./assets/cookie4.png", "./assets/cookie3.png", "./assets/cookie5.png", "./assets/cookie6.png"]

# load audio
clicksound = SoundLoader.load('./assets/buttonsound.wav')
cookiesound = SoundLoader.load('./assets/cookieopen.wav')

# create "grid" layout from kivy and pass it to .kv file
class cookiegrid(Widget):

    # declare variables to match the ids of .kv objects
    cookietext = ObjectProperty(None)
    name = ObjectProperty(None)
    datetime = ObjectProperty(None)
    daily = ObjectProperty(None)
    tsouvelas =  ObjectProperty(None)
    unbox = ObjectProperty(None)
   
    # add fortune cookie button method  
    def btn(self):
        name = self.ids.name.text
        cookiesound.play()
        # create random cookie text based on name
        self.ids.cookietext.text = cookiequotes[randrange(8)].format(name)   
    
    # show random cookie image on button press
    def showimg(self):
        self.ids.myimage.source = cookiedirs[randrange(5)]
   
    # update time method
    def updateTime(self , *args):
        self.ids.datetime.text = time.asctime()

    # open youtube channel link in browser
    def link1(self):
        webbrowser.open("https://www.youtube.com/c/DailyDoseOfInternet")

    def link2(self):
        webbrowser.open("https://www.youtube.com/c/%CE%A4%CF%83%CE%BF%CF%8D%CE%B2%CE%B9")

    def link3(self):
        webbrowser.open("https://www.youtube.com/user/Unboxholics")


# App builder 
class AntiFortuneCookieApp(App):
    def build(self):
        t = cookiegrid()
        # set the clock to be updated every second
        Clock.schedule_interval(t.updateTime, 1)
        return (t)

    # Notepad button functions
    def save(self, notes):
        fob = open('mynotes.txt','w')
        fob.write(notes)
        fob.close() 
        clicksound.play()

    def clear(self, notepad):
        notepad.text = ""
        clicksound.play()
       
# open window and run the app
if __name__ == "__main__":
    AntiFortuneCookieApp().run()
