from tkinter import *
from tkinter import ttk
from tkinter import filedialog
from pytube import YouTube

#Functions
Folder_name = ""
def openLocation():
    global Folder_name
    Folder_name = filedialog.askdirectory()
    if(len(Folder_name) > 1 ):
        downloadLabel.config(text=Folder_name, fg="green")
        DownloadVideo()
    else:
        downloadLabel.config(text="Choose folder to save", fg="red")

def DownloadVideo():
    try:
        choose = ytbChoice.get()
        url = urlEntry.get()

        if(len(url) > 1):
            urlError.config(text="")
            yt = YouTube(url)


            if ( choose == chooses[0]):
                select = yt.streams.filter(progressive=True, file_extension="mp4").get_highest_resolution()
            elif ( choose == chooses[1]):
                select = yt.streams.filter(progressive=True, file_extension="mp4").get_lowest_resolution()
            elif ( choose == chooses[2]) :
                select = yt.streams.filter(only_audio=True).first()
        else:
            urlError.config(text="Paste URL again!", fg="red")
        select.download(Folder_name)
        downloadLabel.config(text="Download Completed!", fg="green")
    except Exception as err:
        print(err)



#UI
root = Tk()
root.title('Youtube Video Downloader')
root.columnconfigure(0, weight=1)#set all content in center

#The title
title = Label(root, text="Youtube video Downloader",
              fg="red",
              font=('jost', 20))
title.grid(row=0, padx=100, pady=25)
urlLabel = Label(root, text="Paste video URL", font=('jost', 15))
urlLabel.grid(row=2)

#URL textbox
urlEntry = Entry(root, width=40, fg="blue", font=("jost", 15))
urlEntry.grid(row=3, pady=20)

#Error Label
urlError = Label(root, text="", fg="red", font=("jost", 13))
urlError.grid(row=4)

choiceLabel= Label(root, text="Chose Type and Quality", font=("jost", 15))
choiceLabel.grid(row=5)

#Combobox
chooses = ["High quality video", "low quality video", "Audio file"]
ytbChoice = ttk.Combobox(root, values=chooses, font=("jost", 15))
ytbChoice.grid(row=6, pady=10)

#Button
downloeadBtn = Button(root, command=openLocation, text="Download", width=20, bg="red", fg="white", font=("jost", 15))
downloeadBtn.grid(row=7, pady=10)

#Error Label
downloadLabel = Label(root, text="", fg="red", font=("jost", 20))
downloadLabel.grid(row=8, pady=10)

root.mainloop()
