# LinkedList

> 
    const LinkedList = function() {
        this.head = null
        this.length = 0
    }
    LinkedList.prototype = {
        constructor: LinkedList,
        _LinkedElement(element) {
            return {
                element,
                next: null
            }
        },
        append(element) {
            let node = this._LinkedElement(element)
            if (head === null) {
                head = item
            } else {
                let current = head
                while (current.next) {
                    current = current.next
                }
                current.next = node
            }
            this.length++
        },
        insert(element, position) {
            if (position < 0 || position > this.length) {
                return false
            }
            let node = this._LinkedElement(element)
            let current = this.head
            let prev
            if (position === 0) {
                head = node
                node.next = current
            } else {
                let index = 0
                while (index++ < position) {
                    prev = current
                    current = current.next
                }
                prev.next = node
                node.next = current
            }
            this.length++
            return true
        },
        remove(element) {
            return this.removeAt(this.indexOf(element))
        },
        removeAt(position) {
            if (position < 0 || position > this.length) {
                return null
            }
            let current = this.head
            let prev
            if (position === 0) {
                this.head = current.next
            } else {
                let index = 0
                while (index++ < position) {
                    prev = current
                    current = current.next
                }
                prev.next = current.next
            }
            this.length--
            return current.element
        },
        indexOf(element) {
            let position = 0
            let current = this.head
            while (current) {
                if (current.element === element) {
                    return position
                }
                position++
                current = current.next
            }
            return -1
        },
        size() {
            return this.length
        },
        isEmpty() {
            return this.length == 0
        },
        toString() {
        },
        getHead() {
            return this.head
        }
    }