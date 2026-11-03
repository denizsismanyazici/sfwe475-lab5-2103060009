Lab 5 notes

1
I think app/tasks/page.tsx will answer /tasks. if I go to /task it will show a 404 page bcs there is no task folder.

it was right, /tasks showed Tasks and /task showed the 404 page.

2
the console.log showed in the terminal where npm run dev runs. the browser console also had it but with a grey Server tag, next just copies it there. for /tasks/1 the type was string not number. I think its bcs the page runs on the server and the id comes from the url, and the url is always text.

3
lang=en tells the screen reader the page is in english so it reads the words with the right pronunciation.

4
with Link there was no new doc request, only a small fetch for the page data and the page didnt load again. with a plain a tag a new document request for / came and all the files loaded again.

5
| route | https | short and readable | lowercase | hyphens not underscores | few query parameters |
|---|---|---|---|---|---|
| / | at deployment | yes | yes | yes | yes, none |
| /tasks | at deployment | yes | yes | yes | yes, none |
| /tasks/[id] like /tasks/1 | at deployment | yes | yes | yes | yes, none |
