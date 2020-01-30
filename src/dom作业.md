
```
window.dom = {
    find(selector,scope){
    return (scope||document).querySelectorAll(selector)
    },
    style(node,object){
        if(argument.length===3){
          node.style[name] = value
        }else if(arguments.length===2){
          if(type of name==='string'){
              return node.style[name]
          }else if(name instance of Object){
               const object = name
               for(let key in object){
                  node.style[key] = object[key]
                } 
            }
        }
    },
    each(divList,fn){
         for(let i=0;i<divList.length;i++){fn.call(null,divList[i])}
        }
        
}
```