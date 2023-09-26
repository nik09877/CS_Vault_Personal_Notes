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
6. collab editor was in infinite loop(because of socket.on('code-change') I was updating state and emitting the same code to other users) , because on editor value change I was emitting the CODE_CHANGE event to other users, and setting my global state again and again, at server I checked if incoming code == server code don't broadcast, also in client side you can create a state called 'received' and set it to true when you receive code via socket.on('code-change') event and if received is set to true don't emit the code.

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
- Fetch problem happening because while hosting on render I made the server wss, so that's why, it should have been https, but if I make it https , web socket will not work


