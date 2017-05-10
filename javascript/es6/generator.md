# generator

> 
    const delay = time => {
        setTimeout( _ => console.log(time), time)
    }
    const generator = function* (){
        yield delay(1000)
        yield delay(2000)
        yield delay(3000)
    }
    let generatorRun = generator()
    generatorRun.next()
    generatorRun.next()
    generatorRun.next()
    generatorRun.next() //{value: undefined, done: true}