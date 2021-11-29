<template>
  <div>copy</div>
</template>

<script>
export default{
  data () {
    return {}
  },
  created () {
    // let obj = {size: '42',age: '20',name: 'jiejie',hobby: {first: 'book',second: 'football'}}
    // let obj2 = obj
    // let obj3 = Object.assign({},obj)
    // obj2.size = '43'
    // obj2.hobby.first = 'backetball'
    // console.log(obj,obj2,obj3,'obj')
    
    let ob={ 
      a:12, b:"sds", 
      preson:{ c:"2", xiao:{ d:1 }},
      fuc:function(){}
    }
    let newObj=this.deepClone(ob)
    newObj.a = 15
    console.log(ob,newObj)
  },
  methods: {
    deepClone (obj) {
      if (obj.construcrtor !== Array && obj.construcrtor !== Object) return obj
      else {
        let targetObj = Array.isArray(obj) ? [] : {}
        if (obj && typeof obj === 'object') {
          for (let key in obj) {
            if (typeof obj[key] === 'object') {
              targetObj[key] = Array.isArray(obj) ? [] : {}
              targetObj[key] = this.deepClone(obj[key])
            } else {
              targetObj[key] = obj[key]
            }
          }
        }
        return targetObj
      }
    },
    clone(obj){
      if(obj.constructor !==Array && obj.constructor !== Object) return obj
      else{
        let targetObj = obj.constructor === Array ? [] : {}
        for(let i in obj){
          if(typeof obj[i]  === 'object'){
            targetObj[i] = obj[i].constructor === Array ? [] : {}; 
            targetObj[i]= this.clone(obj[i])
          }else{
            console.log(obj[i])
            targetObj[i]=obj[i] 
          }
        }
        return targetObj
      }
    }
  }
}
</script>
