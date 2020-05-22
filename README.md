# Oxford-Dictionary
This is a Dictionary written in python, you can search for meanings of any word which is on your mind
------------------------------------------------------------
This is Program in python to basically search for the meaning of any word you wish to search.
I have also added an additional feature to the program ie:- It also shows you suggestion for the closet word for your searched word if in any case you have misspelled or the word does not exist in the dictionary,it will show you the recommendation for that word

This is a simple program where I have used the json module(To import json file) and  the get_close_matches function(To find the closest match) of the difflib module.
The word user is searched in the json file which I am importing in the program and returns the exact meaning of the word searched.

I have uploaded the json file through file upload,feel free to use it.

Code-
```python

import json
from difflib import get_close_matches

def dictionary(word):
 	if word in Jdata:
 		return (Jdata[word])

 	elif word.title() in Jdata:
 		return (Jdata(word.title()))
 	elif word.upper() in Jdata:
 		return (Jdata[word.upper()])
 	elif len(get_close_matches(word,Jdata.keys())) > 0:
 		print("Did you mean %s ???"%get_close_matches(word,Jdata.keys())[0])
 		ask=input("If Yes press y or else press n for No :")
 		if ask == "y":
 			print(get_close_matches(word,Jdata.keys())[0])
 			inst=get_close_matches(word,Jdata.keys())[0]
 			if inst in Jdata:
 				return (Jdata[inst])		
 		elif ask == "n":
 			print("Sorry,could'nt find the word in the dictionary")
 		else:
 			print("You have entered a wrong  input")
 	else:
 		print("Sorry,could'nt find the word in the dictionary")

pass

Jdata=json.load(open('C:/Users/91787/Desktop/Python_Udemy/Dictionary_Content.json'))
word=input("Please enter the word you want to search:")
output=dictionary(word)
if type(output)== list:
	for item in output:
		print(item)
else:
	print(output)
```
