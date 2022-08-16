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

## Linked List

Node

```ts
class Node<T> {
  public next: Node<T> | null = null;
  public prev: Node<T> | null = null;
  constructor(public data: T) {}
}
```

Linked list's methods

```ts
interface ILinkedList<T> {
  insertInBegin(data: T): Node<T>;
  insertAtEnd(data: T): Node<T>;
  deleteNode(node: Node<T>): void;
  traverse(): T[];
  size(): number;
  search(comparator: (data: T) => boolean): Node<T> | null;
}
```

Implement

```ts
class LinkedList<T> implements ILinkedList<T> {
  private head: Node<T> | null = null;

  public insertInBegin(data: T): Node<T> {
    const node = new Node(data);
    if (!this.head) {
      this.head = node;
    } else {
      this.head.prev = node;
      node.next = this.head;
      this.head = node;
    }
    return node;
  }
  
  public insertAtEnd(data: T): Node<T> {
    const node = new Node(data);
    if (!this.head) {
      this.head = node;
    } else {
      const getLast = (node: Node<T>): Node<T> => {
        return node.next ? getLast(node.next) : node;
      };

      const lastNode = getLast(this.head);
      node.prev = lastNode;
      lastNode.next = node;
    }
    return node;
  }
  
  public deleteNode(node: Node<T>): void {
    if (!node.prev) {
      this.head = node.next;
    } else {
      const prevNode = node.prev;
      prevNode.next = node.next;
    }
  }
  
  public traverse(): T[] {
    const array: T[] = [];
    if (!this.head) {
      return array;
    }

    const addToArray = (node: Node<T>): T[] => {
      array.push(node.data);
      return node.next ? addToArray(node.next) : array;
    };
    return addToArray(this.head);
  }
  
  public size(): number {
    return this.traverse().length;
  }
  
  public search(comparator: (data: T) => boolean): Node<T> | null {
    const checkNext = (node: Node<T>): Node<T> | null => {
      if (comparator(node.data)) {
        return node;
      }
      return node.next ? checkNext(node.next) : null;
    };

    return this.head ? checkNext(this.head) : null;
  }
  
  
}
```
