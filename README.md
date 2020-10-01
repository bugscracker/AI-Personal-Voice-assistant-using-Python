	import pyttsx3
	import datetime
	import speech_recognition as sr
	import webbrowser
	import os
	import random

	def take_cmd():
    		r = sr.Recognizer()
    		with sr.Microphone() as source:
        		print("Listening...")
        		#r.pause_threshold = 1
        		audio = r.listen(source)
    		try:
        		print("Recognizing the voice...")
        		query = r.recognize_google(audio, language='en-in')
        
        		if 'open google' in query:
            			webbrowser.open("google.com")

        		elif 'open youtube' in query:
            			webbrowser.open("youtube.com")

        		elif 'open whatsapp' in query:
            			webbrowser.open("web.whatsapp.com")

        		elif 'open github' in query:
            			webbrowser.open("github.com")

        		elif 'open Google Classroom' in query:
            			webbrowser.open("classroom.google.com/u/0/h")

        		elif 'Google Classroom' in query:
            			webbrowser.open("classroom.google.com/u/0/h")

       	 		elif 'who are you' in query:
            			speak("I am your personal assistant, soofia....")
        
        		elif 'play music' in query:
            			music_dir = 'C:\\Users\\bugscracker\\Music'
            			songs = os.listdir(music_dir)
            			# print(songs)
            			n = random.randint(1, 26)
            			os.startfile(os.path.join(music_dir, songs[n]))
        
        		elif 'time please' in query:
            			strTime = datetime.datetime.now().strftime("%H:%M:%S")
            			print(strTime)
            			speak(f"Rajkumar, the time is {strTime}")

        		elif 'open notepad' in query:
            			codePath = "C:\\WINDOWS\\system32\\notepad.exe"
            			os.startfile(codePath)

       		 	elif 'open crome' in query:
            			codePath = "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            			os.startfile(codePath)

        		elif 'open code' in query:
            			codePath = "C:\\Program Files\\Microsoft VS Code\\Code.exe"
            			os.startfile(codePath)

		        elif 'open pycharm' in query:
            			codePath = "C:\\Program Files\\JetBrains\\PyCharm 2019.2.4\\bin\\pycharm64.exe"
            			os.startfile(codePath)
        
        		elif 'wikipedia' in query:  # if wikipedia found in the query then this block will be executed
            			speak('Searching Wikipedia...')
           	 		query = query.replace("wikipedia", "")
           			results = wikipedia.summary(query, sentences=2)
            			speak("According to Wikipedia")
            			print(results)
            			speak(results)

    		except Exception as e:
        		print(e)
        		print("Say it clearly...")
        		return "none"
    		return query
	while True:
    		take_cmd()
