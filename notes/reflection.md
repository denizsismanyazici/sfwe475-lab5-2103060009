Lab 5 reflection

1
page.tsx has no use client and only gets the tasks with await on the server, it doesnt need clicks or state. TaskBoard needs useState and clicks which only work in the browser, so it has use client.

2
on /tasks view source had the task titles inside the html bcs next made the page on the server. in my Lab 4 vite app it only had an empty div id root bcs react builds everything in the browser after the js loads.

3
it breaks lowercase (the capital T in Tasks) and hyphens not underscores (Project_Plan). I would rename it to /tasks/project-plan.
