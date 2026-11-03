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

6
prediction: I think /tasks will give an error bcs TaskBoard uses useState and useEffect but it doesnt have use client, so next tries to run it on the server.

it was right. the error was:
Error: You're importing a module that depends on `useEffect` into a React Server Component module. This API is only available in Client Components. To fix, mark the file (or its parent) with the `"use client"` directive.

in my words: pages in next are server components by default, and the server cant use useState or useEffect bcs they only work in the browser. so I have to say this file is a client component with use client.

7
the console.log from TasksPage showed in the terminal where npm run dev runs, the browser console only had a copy with the Server tag. typeof window was undefined, so the server component runs on the server in node and not in the browser, bcs window only exists in the browser.

8
on /tasks view source already has the task titles like Read Chapter 4 inside the html. in my Lab 4 vite app view source only has an empty div id root and a script, no titles. its bcs next makes the html on the server with the tasks inside, but vite sends an empty page and react builds everything in the browser after.

9
| File | Server or Client? | Reason |
|---|---|---|
| app/layout.tsx | Server | it has no use client and only makes the html and the nav, it doesnt need state or clicks |
| app/tasks/page.tsx | Server | it has no use client and its async, it gets the tasks on the server with fetchTasks |
| TaskBoard.tsx | Client | it has use client bcs it uses useState for the tasks and the filter |
| TaskList.tsx and TaskCard.tsx | Client | they dont have use client but TaskBoard imports them so they become client code |
| FilterBar.tsx and NewTaskForm.tsx | Client | TaskBoard imports them, they have clicks and NewTaskForm uses useState |

only TaskBoard.tsx needed use client written in it. TaskList, TaskCard, TaskCheckbox, FilterBar and NewTaskForm are client code only bcs TaskBoard imports them.

10
Route (app)
┌ ○ /
├ ○ /_not-found
├ ○ /tasks
└ ƒ /tasks/[id]

○  (Static)   prerendered as static content
ƒ  (Dynamic)  server-rendered on demand

/tasks is static, so the html with the tasks is made only one time at build. if the tasks changed every minute people would still see the old tasks from build time until we build again.

11
a) a public page for one shared task: server. search engines must see it and its public, so the server makes the html with the task inside.
b) a drag and drop planning board: browser. search engines dont need it, its private and very interactive so it can run in the browser.
c) an about page: ahead of time. search engines must see it but it almost never changes, so it can be made once at build.

12
rel=sponsored tells the search engine the link is paid, like an ad. rel=ugc tells the search engine the link was added by a user, not by us.
