- 
- About persisting user id
    - blackboard
        - @X@user.id@X@
        - @X@user.batch_uid@X@
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2Fjs2yBGN3oh.png?alt=media&token=477b0cda-5b08-48e3-8788-587efb6bdd09)
    - canvas
        - JCU and Aston might not allow for 
        - https://twu.beta.instructure.com/courses/2904707/pages/week-6-overview
        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2Fqj7Bu4UdK2.png?alt=media&token=b0bb577a-622f-4319-9a5a-38bbe7c8b357)
        - ```javascript
function getLoggedInUser(){
  return $.get("/api/v1/users/self").then(data => data).then(res => res)
}

function appendToAllIframesSrc(value){
  document.querySelectorAll("iframe.userDataTarget").forEach(iframe => {
    let {src} = iframe;
    src = src + "?username=" + value;
    iframe.src = src;
  })
}```
    - moodle
        - 
