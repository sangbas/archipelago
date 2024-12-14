# Archipelago

**Basic Questions**

```
Logic: We can add status as flag. If status = 'DRAFT' then photo is not published and need to be reviewed. Else if status = 'PUBLISHED' then photo is published

Technologies: Lambda, RDS, S3

Data structure: id, path, user_id, created_at, status, reviewer_id, reviewed_at
```

**Database Questions**

* **Level 1**
  ```
  SELECT count(CustomerID) FROM Customers where Country = 'Germany';
  ```
* **Level 2**
  ```
  SELECT COUNT(CustomerID), Country 
  FROM Customers 
  GROUP BY Country 
  HAVING COUNT(CustomerID) >= 5 
  ORDER BY COUNT(CustomerID) DESC;
  ```
* **Level 3**
  ```
  SELECT CustomerName, OrderCount, FirstOrder, LastOrder 
  FROM ( SELECT Orders.CustomerID, COUNT(OrderID) as OrderCount, FIRST(FORMAT(OrderDate,"yyyy-MM-dd")) as FirstOrder, LAST(FORMAT(OrderDate,"yyyy-MM-dd")) as LastOrder FROM Orders GROUP BY Orders.CustomerID ) AS t1 INNER JOIN Customers ON t1.CustomerID=Customers.CustomerID 
  WHERE OrderCount >= 5 
  ORDER BY LastOrder DESC;
  ```

**JavaScript/TypeScript Questions**

* **Level 1:**
  ```
  function titleCase(title: string): string {
    return title.split(' ')
     .map(w => w[0].toUpperCase() + w.substring(1).toLowerCase())
     .join(' ');
  }
  ```
* **Level 2**
  ```
  function delay(ms) {
    return new Promise(resolve =>
      setTimeout(resolve, ms)
    );
  }
  ```

* **Level 2.5**
  ```
  async function fetchData(url) {
      return new Promise((resolve, reject) => {
          setTimeout(() => {
              if(!url) {
                reject('URL is required');
              } else {
                resolve(`Data from ${url}`);
              }
          }, 1000);
      });
  }
  
  async function processData(data) {
    return new Promise((resolve, reject) => {
          setTimeout(() => {
              if(!data) {
                reject('Data is required');
              } else {
                resolve(data.toUpperCase());
              }
          }, 1000);
      });
  }
  
  async function run() {
    try {
      const response = await fetchData("https://example.com");
      const data = await processData(response);
      console.log("Processed Data:", data);
    } catch(error) {
      console.error("Error:", error);
    }
  }
  
  run();
  ```

* **Level 3-4**
  
  * Chat client: https://github.com/sangbas/websocket-chat
  * Chat server: https://github.com/sangbas/websocket-chat 
  * Chat app: http://18.141.137.138:3000
  

**Vue.js**

1. Explain Vue.js reactivity and common issues when tracking changes.
   * Reactivity is **the mechanism that allows the framework to detect when data used on the page is changed (mutated), and to update the page optimally to reflect these changes**.
2. Describe data flow between components in a Vue.js app
   * **Parent to Child (Props)**:  Data can be passed from a parent component to a child component using props. The parent defines the props and provides the data. The child component receives these props as its properties.
   * **Child to Parent (Events)**: Child components can communicate with their parent components by emitting events. The parent listens for these events using the `v-on` directive and can handle them accordingly.
3. List the most common cause of memory leaks in Vue.js apps and how they can be solved.
   * Event Listeners
     * **Cause**: Components may add event listeners but fail to remove them when the component is destroyed.
     * **Solution**: Use `beforeDestroy` or `onBeforeUnmount` lifecycle hooks to remove any event listeners.
   * Timers and Intervals
     * **Cause**: Using `setTimeout` or `setInterval` without clearing them can lead to memory leaks if the component is destroyed before the timer completes.
     * **Solution**: Clear any timers or intervals in the `beforeDestroy` or `onBeforeUnmount` hook.
4. What have you used for state management
   * Vuex (a state management library) can be used to manage and centralize the state. Components can access the shared state or commit mutations to change the state.
5. What's the difference between pre-rendering and server side rendering?
   * The difference is in when it generates the HTML for a page. Static Generation is the pre-rendering method that generates the HTML at build time. The pre-rendered HTML is then reused on each request. Server-side Rendering is the pre-rendering method that generates the HTML on each request.

**Website Security Best Practises**

1. Ensure access control
2. Use latest crypthographic
3. Avoid script injection (SQL & XSS)
4. Maintain component or library version
5. Avoid sensitive data exposure

**Website Performance Best Practises**

1. Use CDN
2. Optimize images
3. Browser Caching
4. Limit the use of external scripts
5. Minify CSS and javascript
6. Reduce HTTP requests
7. Database indexing
8. Load balancing
9. Asynchronous processing

**Golang**

```
func WordFrequency(str string) map[string]int {
	dict := make(map[string]int)
	regex := regexp.MustCompile("[^A-Za-z0-9_-]")
	words := regex.Split(str, -1)

	for _, word := range words {
		dict[strings.ToLower(word)]++
	}
	return dict
}
```

**Tools**

* Git - 4
* Redis - 5
* VSCode / JetBrains - 5
* Linux - 4
* AWS
  
  * EC2 - 3
  * Lambda - 3
  * RDS - 3
  * Cloudwatch - 3
  * S3 - 3
* Unit testing - 4
* Kanban boards - 5

