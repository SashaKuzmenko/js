# js карринг
var bind = function (arg1) {
    var arity = arg1.length
  
    return function arg2(...args) {
      console.log('arg2 args', args)
      if (args.length >= arity) {
        console.log('enough arguments')
        return arg1(...args)
      } else {
        console.log('more arguments')
        return function arg3(...moreArgs) {
          console.log('arg3', moreArgs)
          var newArgs = args.concat(moreArgs)
          return arg2(...newArgs)
        }
      }
    }
  }
  var abc = function (a, b, c, d, e, f) {
    return a + b + c + d + e + f 
  }
  var curriedAdd = bind(abc)
  console.log(curriedAdd(1,2,3)(4,5,6))
