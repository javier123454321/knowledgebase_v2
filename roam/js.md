- {{roam/js}}
    - ```javascript
function formatDateObjToRoam(date){
  const month = date.getMonth() > 8 ? (date.getMonth() + 1) : ('0' + (date.getMonth() + 1))
  const day = date.getDate() > 9 ? date.getDate() : ('0' + date.getDate())
  return month + '-' + day + '-' + date.getFullYear();
}

(() => {
  const template = ["[[Gratitude List]]", 
                    "[[Quick Capture]]", 
                    "[[Literature Notes]]",
                    "((JQhXos4YD))",
                   	"((FD8pp4xDf))"];
  
  template.reverse()
  template.forEach(block =>{
	window
  	.roamAlphaAPI
  	.createBlock(
	{"location": 
		{"parent-uid": formatDateObjToRoam(new Date()), 
		 "order": 0}, 
	 "block": {"string": block}
    })
  })
})()```
