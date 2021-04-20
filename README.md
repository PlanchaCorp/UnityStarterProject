# LD48

## Configure Unity for Git

*[Instructions taken from here](https://thoughtbot.com/blog/how-to-git-with-unity)  
* Make the .meta files visible to avoid broken object references:
  * Go to *Edit > Project Settings > Editor*
  * In *Version Control*, select *Mode: "Visible Meta Files"*
* Use plain text serialization to avoid unresolvable merge conflicts
  * In *Asset Serialization*, select *Mode: "Force Text"*
Save your changes using *File > Save Project*  

