1. In `FileUploading.jsx` while downloading code we need to do this for it to work in `FireFox`
```javascript
//DOWNLOAD CODE

  const TextFile = () => {
    const element = document.createElement('a');
    const file = new Blob([code], { type: 'text/plain' });

    element.href = URL.createObjectURL(file);
    element.download = 'CollabCodePro.txt';
    // Required for this to work in FireFox
    document.body.appendChild(element); 
    element.click();
  };
```
2. Read about yjs ydoc and y-webrtc and signalling servers
3. In node server was trying to access a env variable without requiring dotenv.config()
4. react-graph-vis Graph is not working
5. Couldn't parse Leetcode problems

#### CONTEST WORLFLOW
```cpp
 * If FIRST USER JOINS WE CREATE A CONTEST

 * ELSE WE ALLOW THE USER TO JOIN THE CONTEST IF CONTEST HASN'T STARTED YET

 * WHEN WE DO START THE CONTEST WE FETCH ALL PROBLEMS USING AXIOS

 * THEN WE SEND THOSE PROBLEMS TO CLIENTS

 * WHEN SOMEONE WANTS TO SEE LEADERBOARD

 * WE CHECK WHICH PROBLEMS HAVEN'T BEEN SOLVED YET

 * THEN FOR EACH PROBLEM WE CHECK WHICH USER HAS SOLVED IT FIRST

 * THEN WE UPDATE THE PROBLEM DATA AND RATING OF USERS PARTICULARLY

 * AND RETURN THE RESULTS
```
- When a user leaves from collab-draw I wasn't removing all the cursors from it's state , so whenever he joins a new room those old cursors were displaying , so when leaving clear the cursors in its store.

