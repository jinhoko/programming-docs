# Programming Concepts and Scala

OOP와 functional programming의 concept이 모두 반영되어 있는 Scala 언어를 배우면서, Software design concept과 programming에 대한 전반적인 고민을 해볼 수 있었다.


*(틀린 게 있을 수 있다)*

## Five Key Questions

### What is the real power of OOP?
Stateful

### What is the real power of Functional Programming?
Stateless

### What is the real power of Type Theory?
Type inference
Pattern matching

### What is the real power of Traits?
scala의 trait은 java의 interface와 개념적으로 유사한 것으로 대응되는데, 우선 사실부터 얘기하자면 trait은 interface보다 무조건 더 powerful하다.
그 이유는, trait은 interface가 하는 일을 모두 다 할 수 있지만, 역은 성립하지 않기 때문이다.
구현의 관점에서 봤을 때, trait가 프로그램의 구현에 있어 더 유연하게 사용될 수 있다.

단어의 의미를 생각해보면, interface는 말 그대로 객체의 인터페이스를 정의하는 것이다.
Trait는 성질, 특성이라는 의미를 가진다. 즉 trait을 정의하는 것은 그 객체의 성질을 정의하는 것을 의미한다.


trait가 interface에 비해 허용하는것 :
- trait mixin ; it's a composition of characteristics
- 내부의 함수 구현이 허용됨 ; 불필요한 코드를 객체 내에서 다 작성할 필요가 없음.

interface는 자칫 over-structured될 수 있다고 생각한다. interface는 프로그램 명세서에 가까우므로, 대부분의 클래스 정의와 함께 다 쓰는게 convention이 될 것 같은데, 굳이 꼭 interface의 정의가 필요하지 않은 class도 있다. trait의 선택적 사용을 통해 over-structured program을 피할 수 있을 것이라고 생각한다.

생각되는 단점은, code 전반적으로 구조가 약해질 수 있다는 것인데, trait + functional programming 의 도입을 통해 절약한 code lines나, 구현 과정에서 structure의 modification에 따른 code rewriting에 투입되는 time cost를 고려한다면 전혀 단점이 될 것 같지 않다.


### How are these power revealed in Scala language?


Functional programming이 자유롭게 사용되는 scala language가 최근의 트렌드와 어울리지 않는 것도 아니다. Functional programming이 산업 많은 분야에서도 사용되고 있으며, scala 언어는 아니지만 javascript의 FP component라던지(Scheme 언어에서 참고했다고 함.), Android의 Official supported language가 된 Kotlin 언어도 FP의 요소들을 많이 가지고 있다.
Big data systems에서도 적극적으로 활용될 수 있는데, Apache Spark의 transformation이 그것이다. Apache Spark의 주된 연산 패러다임으로써, 기본적으로 RDD라는 in-memory dataset의 각 item에 사용자가 제시한 function을 적용해 연산을 하는 방식으로 구현된다. 여기서 FP의 higher-order function 개념이 너무나 자연스럽게 도입될 수 있으며, parallelism을 적용하는 데 있어서도 imperative programming에 비해 훨씬 자연스럽다고 생각한다. 


## References
- https://thomasbandt.com/who-cares-about-functional-programming
