---
created: 2023-11-15T20:51
updated: 2023-11-15T20:51
---
# vue2

## [vuejs](https://blog.csdn.net/zemprogram/article/details/103404763)

### [双向数据绑定：讲得很优秀，有时间可以重点研究下](https://www.w3cplus.com/vue/vue-two-way-binding-object-defineproperty.html)

### [双方数据绑定原理分析：讲得也不错](https://blog.csdn.net/zemprogram/article/details/103404763)

### [手动实现双向数据绑定：一般](https://www.jianshu.com/p/e7ebb1500613)

### [vue原理分析：一般](https://github.com/answershuto/learnVue/blob/master/docs/%E5%93%8D%E5%BA%94%E5%BC%8F%E5%8E%9F%E7%90%86.MarkDown)

### [双向数据绑定：一般](https://developer.aliyun.com/ask/288775)

## vuex

## iview ui 

## element ui

### [遇到一个小坑](https://blog.csdn.net/weixin_34234823/article/details/87974959)

- [checkbox-group组件响应change事件的时机是延迟到下次DOM更新循环之后执行，以为着，这次的点击，在下一次的点击之后，进行判断，如此反复。](https://blog.csdn.net/a654540233/article/details/107245152/)

  this.$nextTick(() => {
            if (this.isGroup) {
              this.dispatch('ElCheckboxGroup', 'change', [this._checkboxGroup.value]);
            }
          });
  this.$nextTick 将回调延迟到下次DOM更新循环之后执行
  
  
  
### 第二个坑

- [form组件在进行重置时，需要调用resetFeilds()这个方法，由于form组件是懒加载的（sync）,所以需要把这个方法的调用放在this.nextTick(()=> this.$refs.form.resetFeilds())，否则会一直报错](https://www.jianshu.com/p/ab8deeaac9d4?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)

- 问题：列表中的数据和弹窗中的数据，如何隔离开来。1.弹窗中进行，列表中的原始数据，不动，弹窗中的显示数据用来读取时映射一下。不改动原始数据。如果要改动，需要深拷贝这个变量。

	- 引发了对深拷贝的处理了

		- JSON.parse(JSON.stringify(data))

			- 这个方法可能有限制

			  JSON.stringify() - JavaScript | MDN (mozilla.org)
			  
	- 实现案例1

		- [实现deepClone的方法1](https://blog.csdn.net/Kimser/article/details/106476775)

		  ···
		  // 深拷贝
		   
		  const clone = (obj) => {
		    var o;
		    // 如果  他是对象object的话  , 因为null,object,array  也是'object';
		    if (typeof obj === 'object') {
		      
		      // 如果  他是空的话
		      if (obj === null) {
		        o = null;
		      }
		      else {
		    
		        // 如果  他是数组arr的话
		        if (obj instanceof Array) {
		          o = [];
		          for (var i = 0, len = obj.length; i < len; i++) {
		            o.push(clone(obj[ i ]));
		          }
		        }
		        // 如果  他是对象object的话
		        else {
		          o = {};
		          for (var j in obj) {
		            o[ j ] = clone(obj[ j ]);
		          }
		        }
		        
		      }
		    }
		    else {
		      o = obj;
		    }
		    return o;
		  };
		   
		  ···
		  
	- 实现案例2

		- [实现deepClone的方法](https://www.jianshu.com/p/2e1768040ecb)

		  ···
		  function deepCopy(obj,cache = []){
		        // 如果为普通数据类型，则直接返回，完成拷贝
		        if (obj===null || typeof obj !== "object"){
		            return obj
		        }
		          // cache用来储存原始值和对应拷贝数据，在递归调用deepCopy函数时，如果本次拷贝的原始值在之前已经拷贝了，则直接返回储存中的copy值，这样的话就不用再循环复制本次原始值里面的每一项了。
		          // 还有一个更为重要的作用，假如原始值里面嵌套两个引用地址相同的对象，使用cache可以保证拷贝出来的copy值里面两个对象的引用地址也相同。
		          // 如果find查找的是一个空数组，则不会执行
		        const hit = find(cache,c=>c.original===obj)
		        if(hit){
		            return hit.copy
		        }
		        // 定义拷贝的数据类型
		        const copy = Array.isArray(obj) ? [] : {}
		        // 用来记录拷贝的原始值和copy值
		        cache.push[{
		            original:obj,
		            copy
		        }]
		        // 递归调用深拷贝函数，拷贝对象中的每一个值
		        Object.keys(obj).forEach(key=>{
		            copy[key]=deepCopy(obj[key],cache)
		        })
		        return copy
		      }
		  ···
		  
			-  const hit1 = find(cache,c=>c.original===obj)

### 封装dialog时

- [从父组件传递dialog开启和关闭的属性like：modalShow，
这种情况下，在dialog关闭时，必须要干一件事情，让父组件知道弹窗是关闭了的，不然下次无法开启。也就是子组件必须要改父组件的值时，该如何实现？](https://blog.csdn.net/weixin_43972992/article/details/103344158)

	- iview中：父组件中用v-model，传递打开和关闭变量到子组件，然后再modal组件关闭时，触发input事件，传递false给变量：简化 => v-model + $emit("input", false)
	- element ui中：父组件中使用:visible.sync="xxShow",子组件触发update:var，传递false过去，简化：=> var.sync + $emit("update:var, false)

### el-tree 中节点的元素的class都是tree-item

## swiper

## [Vue Router](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html#%E5%85%A8%E5%B1%80%E5%89%8D%E7%BD%AE%E5%AE%88%E5%8D%AB)

## vue修改第三方库样式时不生效

### [地址](https://arrow.blog.csdn.net/article/details/107062781)

### 样式穿透不同写法

- 

## 这15个Vue自定义指令，让你的项目开发爽到爆

### [地址](https://zhuanlan.zhihu.com/p/108308393)

## vue自定义指令写法

### Vue.directive('formValidate', {
    bind: function (el, binding, vnode) {
        vnode.componentInstance['formValidator'] = new AsyncValidator(vnode.componentInstance.rules);
    },
    update: function (el, binding, vnode) {
        vnode.componentInstance['formValidator'].validate(vnode.componentInstance.model, (errors) => {
            binding.value(!errors, errors);
        });
    }
});

### vnode.componentInstance

- 指令所在的组件实例

### vnode.componentInstance.model

- 指令所在元素的model属性

## （几乎）完美实现 el-table 列宽自适应

### [地址](https://juejin.cn/post/6865844599613718536)

## 插槽

### [官方文档](https://cn.vuejs.org/v2/guide/components-slots.html)

