# 算法

> 
    const Suanfa = function() {
        this.items = []
    }
    Suanfa.prototype = {
        constructor: Suanfa,
        init(items) {
            this.items = Array.from(items)
        },
        //冒泡排序 复杂度O(n2)
        bubbleSort() {
            let arr = this.items
            let length = arr.length
            for (let i = 0; i < length; i++) {
                for (let j = 0; j < length - 1; j++) {
                    if (arr[j] > arr[j + 1]) {
                        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]
                    }
                }
            }
            console.log(this.items)
        },
        //改进的冒泡排序
        bubbleSortGaijin() {
            let arr = this.items
            let length = arr.length
            for (let i = 0; i < length; i++) {
                for (let j = 0; j < length - 1 -i; j++) {
                    if (arr[j] > arr[j + 1]) {
                        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]
                    }
                }
            }
            console.log(this.items)
        },
        //选择排序 复杂度O(n2)
        selectionSort() {
            let arr = this.items
            let length = arr.length
            let minIndex
            for (let i = 0; i < length - 1; i++) {
                minIndex = i
                for (let j = i; j < length; j++) {
                    if (arr[minIndex] > arr[j]) {
                        minIndex = j
                    }
                }
                if (minIndex != i) {
                    [arr[minIndex], arr[i]] = [arr[i], arr[minIndex]]
                }
            }
            console.log(this.items)
        },
        //插入排序 性能比冒泡排序和选择排序稍好
        insertionSort() {
            let arr = this.items
            let length = arr.length
            let tmp, j
            for (let i = 1; i < length; i++) {
                j = i
                tmp = arr[i]
                while (j > 0 && arr[j - 1] > tmp) {
                    arr[j] = arr[j - 1]
                    j--
                }
                arr[j] = tmp
            }
            console.log(this.items)
        },
        //归并排序 复杂度O(nlogn)
        mergeSort() {
            const mergeSort = (array) => {
                let length = array.length
                if (length === 1) {
                    return array
                }
                let middle = Math.floor(length / 2)
                let left = array.slice(0, middle)
                let right = array.slice(middle, length)
                return merge(mergeSort(left), mergeSort(right))
            }
            const merge = (left, right) => {
                let result = []
                let leftIndex = 0
                let rightIndex = 0
                let leftLength = left.length
                let rightLength = right.length
                while (leftIndex < leftLength && rightIndex < rightLength) {
                    if (left[leftIndex] <= right[rightIndex]) {
                        result.push(left[leftIndex])
                        leftIndex++
                    } else {
                        result.push(right[rightIndex])
                        rightIndex++
                    }
                }
                while (leftIndex < leftLength) {
                    result.push(left[leftIndex])
                    leftIndex++
                }
                while (rightIndex < rightLength) {
                    result.push(right[rightIndex])
                    rightIndex++
                }
                return result
            }
            this.items = mergeSort(this.items)
            console.log(this.items)
        },
        //快速排序 复杂度O(nlogn)
        quickSort() {
            const quickSort = (array, left, right) => {
                if (array.length > 1) {
                    let position = partition(array, left, right)
                    if (left < position - 1) {
                        quickSort(array, left, position - 1)
                    }
                    if (position < right) {
                        quickSort(array, position, right)
                    }
                }
            }
            const partition = (array, left, right) => {
                let priovt = array[Math.floor((left + right) / 2)]
                let i = left
                let j = right
                while (i <= j) {
                    while (array[i] < priovt) {
                        i++
                    }
                    while (array[j] > priovt) {
                        j--
                    }
                    if (i <= j) {
                        [array[i], array[j]] = [array[j], array[i]]
                        i++
                        j--
                    }
                }
                return i
            }
            quickSort(this.items, 0, this.items.length - 1)
            console.log(this.items)
        },
        //二分搜索
        binarySearch(item) {
            this.quickSort()
            let array = this.items
            let low = 0
            let high = this.items.length - 1
            let middle, middleItem
            while (low <= high) {
                middle = Math.floor((low + high) / 2)
                middleItem = array[middle]
                if (item < middleItem) {
                    high = middle - 1
                } else if (middleItem < item) {
                    low = middle + 1
                } else {
                    return middle
                }
            }
            return -1
        }
    }
    ;(() => {
        let suanfa = new Suanfa()
        suanfa.init([1,5,6,3,2,9,8,7,4])
        //suanfa.bubbleSort()
        //suanfa.bubbleSortGaijin()
        //suanfa.selectionSort()
        //suanfa.insertionSort()
        //suanfa.mergeSort()
        //suanfa.quickSort()
        console.log(suanfa.binarySearch(5))
    })()