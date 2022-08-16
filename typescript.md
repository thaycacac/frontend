## List

```ts
class MyList<T> {
    list: T[] = []
    
    checkExist(el: T) {
        for(const item of this.list) {
            if(item === el) return true
        }
        return false
    }
    
    add(item: T) {
        this.list = this.list.concat(item)
    }
    
    remove(el: T) {
        const newList: T[] = []
        if(!this.checkExist(el)) {
            throw new Error(`${el} not exits in list`)
        }
        for(const item of this.list) {
            if(item === el) continue
            newList.push(item)
        }
        this.list = newList
    }
    
    get(index: number) {
        if(index < 0 || index > this.list.length) {
            throw new Error('Over of array')
        }
        return this.list[index]
    }
    
    gets() {
        return this.list
    }
}

const myList = new MyList<number>();

myList.add(1)
myList.add(2)
myList.add(3)
myList.add(4)
myList.remove(2)


console.log(myList.gets())
console.log(myList.get(2))
```
