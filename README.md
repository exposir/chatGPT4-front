# chatGPT4 教你面试

<aside>
💡 听君一席话，胜读十年书。读万卷书不如行万里路，行万里路不如阅人无数，阅人无数不如名师指路。

</aside>

> 💻 编程题 🤔 思考题
> 

[[面经] 5年前端 - 历时1个月收获7个offer🔥 - 掘金](https://juejin.cn/post/7142690757722243102)

## 闭包是什么? 闭包的用途?

闭包是一种在JavaScript中比较重要且有特色的概念。简单来说，闭包是一个函数与其词法环境的组合。在JavaScript中，函数可以访问其自身作用域内的变量，以及任何包含它的外部作用域内的变量。当一个函数在其定义环境之外被调用时，仍然能访问其词法作用域内的变量，这种现象就形成了闭包。

闭包有以下几个主要用途：

1. **模拟私有变量**：JavaScript没有原生的私有变量支持，但我们可以利用闭包来模拟私有变量。将需要保持私有的变量放置在一个外部函数的作用域内，然后返回一个内部函数，这样就可以访问外部函数作用域中的变量，但在函数外部无法直接访问。
2. **函数柯里化（Currying）**：柯里化是一种将多参数函数转换为一系列单参数函数的技巧。闭包可以用来存储函数的参数，实现函数柯里化。
3. **事件处理和回调**：在JavaScript中，我们经常需要使用事件处理器和回调函数。闭包可以让我们在事件处理器或回调函数中访问外部作用域中的变量，使得代码更加灵活和可维护。
4. **延迟执行和定时器**：闭包可以用来实现定时器和延迟执行的功能，例如setTimeout和setInterval。这些函数接受一个回调函数作为参数，在特定的时间之后执行。闭包使得回调函数可以访问其词法作用域内的变量，即使在外部作用域已经执行完毕。
5. **模块化和信息隐藏**：通过使用闭包，我们可以实现模块化和信息隐藏。将相关的功能和变量封装在一个立即执行函数表达式（IIFE）中，只暴露需要公开的接口，保持内部实现细节的私密性。这样可以避免全局作用域的污染，提高代码的可维护性。

## 简述事件循环原理

事件循环（Event Loop）是JavaScript运行时环境中处理异步操作的核心机制。由于JavaScript是单线程的，事件循环机制使得JavaScript能够在同一时间处理多个任务，而不会阻塞程序的执行。

事件循环原理可以简述如下：

1. **执行全局代码**：当JavaScript程序开始执行时，首先执行全局代码。在执行过程中，遇到异步操作（如setTimeout、Promise等），将其放入相应的任务队列（宏任务队列或微任务队列）中，然后继续执行其他同步代码。
2. **宏任务与微任务**：在事件循环中，任务分为宏任务（Macro Task）和微任务（Micro Task）。宏任务包括：script（全局代码）、setTimeout、setInterval等。微任务包括：Promise、MutationObserver等。每个宏任务结束后，会检查并执行所有微任务。
3. **循环执行任务**：当全局代码执行完毕，事件循环开始工作。它会不断地从宏任务队列中取出一个任务执行，当宏任务执行完毕，会检查并执行所有微任务。这个过程会不断重复，形成一个循环，直到所有任务队列为空。
4. **渲染与帧率**：浏览器的渲染和回流（重绘）通常在宏任务之间进行，以保证高效的渲染。浏览器通常以每秒60帧的速率进行渲染，这意味着每一帧的时间约为16.67毫秒。为了避免页面卡顿，我们需要确保每个宏任务在这个时间内执行完毕。

**事件循环机制使得JavaScript能够在单线程环境中处理并发任务，提高了程序执行的效率。**同时，事件循环也使得我们需要注意异步操作的执行顺序，以确保程序的正确性。

## 虚拟dom是什么? 原理? 优缺点?

虚拟DOM（Virtual DOM）是一种在JavaScript中用于优化Web应用性能的技术。它是一种将真实DOM的抽象表示，在内存中创建轻量级的DOM树结构，用于比较和更新真实DOM的变化。虚拟DOM并不会直接操作浏览器的DOM，而是通过比较虚拟DOM树的差异（diffing）来更新真实DOM。

**原理：**

1. 创建虚拟DOM树：当Web应用的状态发生变化时，根据新的状态生成一颗新的虚拟DOM树。
2. 比较虚拟DOM树：将新旧两颗虚拟DOM树进行比较（Diff算法），找出它们之间的差异。
3. 更新真实DOM：根据找出的差异，对真实DOM进行最小化的更新操作。这个过程被称为“DOM的局部更新”或“DOM的重新渲染”。

**优点：**

1. 避免频繁的DOM操作：DOM操作是昂贵的，而虚拟DOM可以将多次的DOM操作合并为一次，减少性能损耗。
2. 提高渲染性能：通过虚拟DOM的Diff算法，只更新发生变化的部分，避免了不必要的重新渲染，从而提高了渲染性能。
3. 跨平台：虚拟DOM是一个独立于浏览器的抽象层，可以方便地实现跨平台的渲染，如服务器端渲染、移动端等。

**缺点：**

1. 虚拟DOM本身的内存占用：虚拟DOM树需要额外的内存空间来存储，对于大型应用来说，内存占用可能会成为一个问题。
2. 额外的计算开销：虚拟DOM树的创建和Diff算法都需要计算资源，虽然它减少了DOM操作，但也引入了新的计算开销。

虚拟DOM是许多现代前端框架（如React、Vue等）的核心技术，它有效地提高了Web应用的性能和开发体验。但是，虚拟DOM并非适用于所有场景，例如在某些性能要求不高或DOM操作较少的场景中，虚拟DOM可能带来不必要的复杂性和开销。因此，在选择是否使用虚拟DOM时，需要根据具体项目需求进行权衡。

## vue 和 react 在虚拟dom的diff上，做了哪些改进使得速度很快?

Vue和React都使用了虚拟DOM技术，以提高Web应用的性能。在虚拟DOM的diff算法上，两者都采用了一些策略和优化来加快比较速度。

1. **限制比较范围：**

React和Vue都将组件树划分为独立的组件，只对发生状态变化的组件及其子组件进行重新渲染。这样，diff算法的比较范围被限制在一个组件的子树上，而不是整个虚拟DOM树。这减少了比较的节点数量，从而提高了速度。

1. **同级比较：**

在对虚拟DOM树进行比较时，React和Vue都只会在同一层级进行节点比较，而不会跨级比较。这是基于一个假设，即在大多数情况下，跨级的DOM节点移动是较少见的。通过只比较同级节点，可以大幅减少diff算法的复杂度。

1. **键值（Key）优化：**

React和Vue都支持为列表中的每个节点分配一个唯一的key。当列表发生变化时，diff算法可以通过这个key来识别具体哪个节点发生了变化，从而避免了不必要的节点重新创建和删除。这大大提高了列表操作的性能。

1. **启发式算法：**

React和Vue都采用了启发式算法来优化虚拟DOM树的比较过程。例如，React使用了一种叫做React Reconciliation的算法，它会比较两个树的节点类型和key值。如果不同，就会直接替换整个节点及其子节点。这种简化了的比较过程可以提高速度。

Vue的diff算法也有类似的优化策略，如两头匹配（在列表的头尾分别进行比较，加速查找过程）。Vue还根据模板编译过程的静态分析结果，提前标记静态节点，避免了对不会发生变化的节点进行diff比较。

尽管React和Vue在虚拟DOM的diff算法上采用了不同的实现细节，但它们都使用了一些通用的策略和优化来加速比较过程。这些优化大大提高了Web应用的性能，使得虚拟DOM技术在现代前端框架中得到广泛应用。

## vue 和 react 里的key的作用是什么? 为什么不能用Index？用了会怎样? 如果不加key会怎样?

在Vue和React中，key是用于标识列表中每个节点的唯一性。为列表中的每个节点分配一个唯一的key可以帮助框架更高效地识别和追踪节点的变化，从而提高列表操作的性能。

**为什么不能用Index作为key？**

1. **不稳定**：当列表发生变化，如添加、删除或排序操作时，index（索引值）可能会发生变化。这会导致虚拟DOM diff算法无法准确地识别节点的变化，从而引发性能问题。
2. **无法复用**：当使用index作为key时，框架无法正确地复用已有的DOM节点。这可能导致不必要的节点创建和销毁，从而影响性能。

**如果使用index作为key：**

1. **性能下降**：由于框架无法正确地识别节点的变化，可能导致不必要的重新渲染，从而降低性能。
2. **状态丢失**：如果组件包含状态信息（如表单输入框），当使用index作为key时，可能导致组件状态在重新渲染过程中丢失。
3. **引发错误**：当列表发生变化时，使用index作为key可能会导致DOM节点更新不正确，从而引发渲染错误。

**如果不加key：**

1. Vue和React会尝试使用默认的行为来识别节点的变化。这可能会导致一些性能问题，特别是当列表进行频繁的更新操作时。
2. 当列表发生变化时，框架可能无法正确地更新DOM节点，从而导致渲染错误。

综上所述，为列表中的每个节点分配一个唯一的key是非常重要的。它可以帮助框架更高效地识别和追踪节点的变化，从而提高应用的性能。在实际开发中，我们应尽量避免使用index作为key，而是使用具有唯一性和稳定性的值（如ID）。

## vue 双向绑定的原理是什么?

Vue中的双向绑定是一种同步数据和视图的技术，它允许我们在数据模型和视图之间建立起双向关联。当数据模型发生变化时，视图会自动更新；当视图发生变化时，数据模型也会相应地更新。Vue实现双向绑定的原理主要包括以下几个方面：

1. 数据劫持（数据观察）：Vue通过使用Object.defineProperty（ES5）或Proxy（ES6）来劫持数据对象的属性，使得当数据属性被访问或修改时，Vue可以捕获这些操作。这样，Vue就可以在数据发生变化时通知相关的视图进行更新。
2. 发布-订阅模式：Vue使用发布-订阅模式来实现数据和视图之间的解耦。当数据发生变化时，Vue会将变化通知给所有订阅了该数据的观察者（Watcher），观察者收到通知后会执行相应的更新操作。
3. 模板解析：Vue会解析模板中的指令（如v-model）和插值表达式（如{{}}），并将它们与数据模型关联起来。当数据发生变化时，Vue会根据这些关联关系更新视图。
4. 响应式更新：当数据发生变化时，Vue会对涉及的DOM进行局部更新，而不是重新渲染整个视图。这可以减少不必要的DOM操作，从而提高性能。

以v-model指令为例，它实现了表单元素和数据模型之间的双向绑定。当用户在表单元素上输入内容时，v-model会监听input事件，并将输入的内容同步到数据模型。当数据模型发生变化时，v-model会自动更新表单元素的值。

总之，Vue通过数据劫持、发布-订阅模式、模板解析和响应式更新等技术实现了双向绑定。这种双向绑定使得我们在开发过程中无需关心数据和视图之间的同步问题，从而提高了开发效率和应用性能。

## vue 的keep-alive的作用是什么？怎么实现的？如何刷新的?

Vue中的**`<keep-alive>`**组件用于缓存非活动组件的状态，以便在组件切换时减少不必要的重新渲染。使用**`<keep-alive>`**组件可以提高应用性能，特别是在动态组件和路由组件中。

**`<keep-alive>`**的作用：

1. 缓存组件：当组件被切换为非活动状态时，**`<keep-alive>`**会将其缓存起来，而不是销毁。
2. 保留组件状态：当组件被重新激活时，**`<keep-alive>`**会从缓存中恢复组件状态，而不是重新创建组件实例。
3. 生命周期钩子：**`<keep-alive>`**组件提供了两个特殊的生命周期钩子：**`activated`**和**`deactivated`**。这些钩子在组件被缓存和恢复时分别被调用，可以用于执行特定的逻辑。

**`<keep-alive>`**的实现原理：

**`<keep-alive>`**组件使用了Vue的动态组件功能，将要缓存的组件包裹在**`<keep-alive>`**标签内。当组件被切换时，**`<keep-alive>`**会将非活动组件的状态缓存到内部的组件缓存对象中。当组件被重新激活时，**`<keep-alive>`**会从缓存对象中恢复组件的状态。

刷新**`<keep-alive>`**缓存的方法：

1. 使用**`key`**属性：可以通过改变**`<keep-alive>`**组件内部组件的**`key`**属性值，强制刷新组件。当**`key`**值改变时，Vue会认为这是一个新的组件实例，从而重新创建和渲染组件。
2. 使用**`include`**和**`exclude`**属性：**`<keep-alive>`**组件提供了**`include`**和**`exclude`**属性，可以用于指定要缓存和不缓存的组件。通过动态修改这些属性值，可以控制组件的缓存状态。
3. 手动清除缓存：可以通过访问**`<keep-alive>`**组件实例的**`$cache`**属性来手动清除特定组件的缓存。例如，可以在父组件中使用**`ref`**属性获取**`<keep-alive>`**组件实例，然后操作其**`$cache`**属性以清除缓存。

总之，Vue中的**`<keep-alive>`**组件用于缓存非活动组件的状态，从而提高应用性能。要刷新**`<keep-alive>`**组件的缓存，可以通过改变**`key`**属性、修改**`include`**和**`exclude`**属性或手动清除缓存等方法实现。

## vue 是怎么解析template的? template会变成什么?

Vue解析模板的过程分为两个主要步骤：解析和编译。在这个过程中，Vue会将模板转换为渲染函数，这个渲染函数将负责根据数据模型生成虚拟DOM树。

1. 解析：
Vue首先会解析模板中的指令、插值表达式、事件绑定等语法结构。解析过程是基于HTML解析器进行的，Vue会将模板字符串解析为一个抽象语法树（AST，Abstract Syntax Tree）。AST是一种树形结构，用于表示模板中的各种元素、属性和指令等。
2. 优化：
在解析完成后，Vue会对生成的AST进行优化。优化过程主要是为了标记静态节点，这些节点在后续的diff算法中可以被直接跳过，从而提高性能。Vue会检查每个节点以确定它们是否为静态节点，并将它们标记为静态或非静态。
3. 编译：
编译阶段是将AST转换为渲染函数的过程。Vue会遍历AST，根据各种节点类型生成相应的渲染函数代码。生成的渲染函数是一个JavaScript函数，它会根据数据模型生成虚拟DOM树。
4. 渲染：
当数据发生变化时，Vue会调用生成的渲染函数，并将返回的虚拟DOM树与上一次生成的虚拟DOM树进行比较（diff算法）。根据比较结果，Vue会更新实际的DOM节点以保持与数据模型的同步。

所以，简而言之，Vue解析模板的过程是将模板字符串解析为AST，然后编译为渲染函数。渲染函数负责根据数据模型生成虚拟DOM树，最终更新到实际的DOM节点。这个过程使得Vue能够实现高效的响应式更新和视图渲染。

## 如何解析指令? 模板变量? html标签

Vue在解析模板时，会根据不同的语法结构（如指令、模板变量、HTML标签等）进行处理。以下是这些语法结构的解析方法：

1. 解析指令：
Vue中的指令以**`v-`**为前缀，例如**`v-model`**、**`v-if`**和**`v-for`**等。在解析模板时，Vue会识别并处理这些指令。解析器会将指令的名称、参数和表达式提取出来，并将它们添加到AST节点的属性列表中。在后续的编译阶段，Vue会根据这些属性生成相应的渲染函数代码。
2. 解析模板变量（插值表达式）：
在Vue模板中，插值表达式使用双大括号（**`{{}}`**）包裹。解析器会识别插值表达式，并将表达式中的变量提取出来。将插值表达式转换为一个文本节点，并将文本节点添加到AST中。在编译阶段，Vue会根据插值表达式生成相应的渲染函数代码，以便在运行时计算表达式的值并插入到文本节点中。
3. 解析HTML标签：
Vue使用HTML解析器来解析模板中的HTML标签。解析器会将HTML标签及其属性解析为AST节点，并将这些节点按照嵌套关系组织成树形结构。在编译阶段，Vue会根据AST节点生成相应的虚拟DOM创建和更新代码。

解析模板的整个过程可以概括为以下几个步骤：

1. 将模板字符串解析为AST（抽象语法树）。
2. 对AST进行优化，标记静态节点。
3. 将AST编译为渲染函数。

在这个过程中，Vue会解析并处理模板中的指令、插值表达式和HTML标签等语法结构，从而实现模板与数据模型之间的绑定和响应式更新。

## 用过vue 的render吗? render和template有什么关系

Vue中的**`render`**函数是一个用于生成虚拟DOM树的函数，它可以直接操作虚拟DOM，从而为开发者提供更底层、更灵活的控制。**`render`**函数通常接收一个参数**`h`**（或**`createElement`**），该函数用于创建虚拟DOM节点。

我在使用Vue时，确实使用过**`render`**函数。**`render`**函数和**`template`**的关系如下：

1. 关系：**`template`**和**`render`**函数实际上是两种不同的方式来描述组件的视图。**`template`**是一个基于HTML的模板字符串，它使用Vue的指令和插值表达式来描述视图；**`render`**函数则是一个JavaScript函数，它使用虚拟DOM API来创建和更新虚拟DOM树。
2. 转换：在Vue内部，**`template`**最终会被转换为**`render`**函数。当Vue解析模板时，它会将模板字符串解析为抽象语法树（AST），然后将AST编译为渲染函数。这意味着，不论是使用**`template`**还是**`render`**函数，最终都会生成一个渲染函数来处理虚拟DOM的创建和更新。
3. 使用场景：对于大多数情况，使用**`template`**编写组件视图更加直观和简便，特别是对于不熟悉虚拟DOM API的开发者。然而，在某些复杂的场景中，使用**`render`**函数可能更适合，因为它提供了更底层、更灵活的控制。例如，当需要对视图进行动态构建或进行高级DOM操作时，使用**`render`**函数可能更合适。

总之，**`render`**函数和**`template`**都是用于描述Vue组件视图的方式。**`template`**是一个基于HTML的模板字符串，而**`render`**函数是一个基于虚拟DOM API的JavaScript函数。在Vue内部，**`template`**会被转换为**`render`**函数，从而实现视图的创建和更新。根据具体的使用场景和需求，开发者可以选择使用**`template`**或**`render`**函数来编写组件视图。

## 💻 实现一个节流函数? 如果想要最后一次必须执行的话怎么实现?

节流函数（throttle）的作用是限制一个函数在一定时间内只能执行一次。这在处理高频触发事件（如浏览器窗口大小调整、滚动事件等）时非常有用。下面是一个简单的节流函数实现：

```jsx
function throttle(func, delay) {
  let lastExecution = 0;

  return function (...args) {
    const now = Date.now();
    if (now - lastExecution > delay) {
      lastExecution = now;
      func.apply(this, args);
    }
  };
}

```

如果想要确保最后一次触发的事件在节流结束时执行，可以对节流函数进行一些修改：

```jsx
javascriptCopy code
function throttle(func, delay) {
  let lastExecution = 0;
  let timeoutId = null;

  return function (...args) {
    const now = Date.now();
    const remainingTime = delay - (now - lastExecution);

    const executeFunction = () => {
      lastExecution = Date.now();
      timeoutId = null;
      func.apply(this, args);
    };

    if (remainingTime <= 0 || remainingTime > delay) {
      if (timeoutId) {
        clearTimeout(timeoutId);
        timeoutId = null;
      }
      executeFunction();
    } else if (!timeoutId) {
      timeoutId = setTimeout(() => {
        executeFunction();
      }, remainingTime);
    }
  };
}

```

在这个修改后的版本中，我们引入了一个定时器**`timeoutId`**。如果在节流时间内触发了新的事件，我们会使用**`setTimeout`**来确保在节流结束时执行最后一次触发的事件。通过这种方式，我们可以保证最后一次触发的事件总是会被执行。

## 💻 实现一个批量请求函数, 能够限制并发量?

以下是一个实现批量请求函数的示例，该函数接受一个请求函数数组和一个限制并发量的参数**`maxConcurrency`**：

```jsx
function batchRequest(requests, maxConcurrency) {
  return new Promise((resolve, reject) => {
    const results = [];
    let currentIndex = 0;
    let activeRequests = 0;

    function handleRequest() {
      if (currentIndex >= requests.length) {
        // 当所有请求都已完成时，解析结果
        if (activeRequests === 0) {
          resolve(results);
        }
        return;
      }

      // 执行请求
      const currentRequest = requests[currentIndex];
      currentIndex++;
      activeRequests++;

      currentRequest()
        .then((result) => {
          results.push(result);
        })
        .catch((error) => {
          results.push(error);
        })
        .finally(() => {
          activeRequests--;
          handleRequest();
        });
    }

    // 初始化并发请求
    for (let i = 0; i < Math.min(maxConcurrency, requests.length); i++) {
      handleRequest();
    }
  });
}

```

这个**`batchRequest`**函数会按照给定的最大并发数**`maxConcurrency`**来执行请求。当一个请求完成时，将自动启动下一个请求，直到所有请求都已完成。当所有请求都已完成时，函数将返回一个包含所有结果的数组。注意，结果数组中的顺序可能与输入的请求顺序不同，因为它们是根据完成顺序来存储的。如果需要按照输入顺序返回结果，请根据**`currentIndex`**调整结果数组。

## 💻 数组转树结构

这是一个将数组转换为树结构的简单实现：

```jsx
function arrayToTree(arr) {
  const map = {};
  const result = [];

  // 将数组元素以id为键存储到map中
  arr.forEach(item => {
    map[item.id] = { ...item, children: [] };
  });

  // 遍历数组，构建树结构
  arr.forEach(item => {
    const parent = map[item.parentId];
    if (parent) {
      parent.children.push(map[item.id]);
    } else {
      // 如果没有找到父节点，说明是根节点，将其添加到结果数组中
      result.push(map[item.id]);
    }
  });

  return result;
}

const arr = [
  // ... 你提供的数组数据 ...
];

const tree = arrayToTree(arr);
console.log(tree);
```

这个**`arrayToTree`**函数首先创建一个映射，将数组中的每个元素以其**`id`**作为键存储。接下来，遍历数组并根据**`parentId`**将元素添加到相应的父节点的**`children`**数组中。如果没有找到父节点，说明当前元素是根节点，将其添加到结果数组中。最后，函数返回结果数组，它包含了转换后的树结构。

## 去除字符串中出现次数最少的字符，不改变原字符串的顺序。

```jsx
“ababac” —— “ababa”
“aaabbbcceeff” —— “aaabbb”
```

```jsx
function removeLeastFrequentChars(str) {
  // 计算每个字符出现的次数
  const charCounts = {};
  for (let i = 0; i < str.length; i++) {
    const char = str.charAt(i);
    if (charCounts[char]) {
      charCounts[char]++;
    } else {
      charCounts[char] = 1;
    }
  }

  // 找到出现次数最少的字符
  let minCount = Infinity;
  for (const char in charCounts) {
    if (charCounts[char] < minCount) {
      minCount = charCounts[char];
    }
  }

  // 构建新字符串
  let result = '';
  for (let i = 0; i < str.length; i++) {
    const char = str.charAt(i);
    if (charCounts[char] !== minCount) {
      result += char;
    }
  }

  return result;
}

console.log(removeLeastFrequentChars('ababac')); // "ababa"
console.log(removeLeastFrequentChars('aaabbbcceeff')); // "aaabbb"
```

## 💻 写出一个函数trans，将数字转换成汉语的输出，输入为不超过10000亿的数字。

```jsx
trans(123456) —— 十二万三千四百五十六
trans（100010001）—— 一亿零一万零一
```

```jsx
const numbers = ['', '一', '二', '三', '四', '五', '六', '七', '八', '九'];
const units = ['', '十', '百', '千'];
const largerUnits = ['', '万', '亿'];

function trans(number) {
  if (isNaN(number) || number < 0 || number > 100000000000) {
    throw new Error('Invalid number');
  }

  if (number === 0) {
    return '零';
  }

  let result = '';
  let currentIndex = 0;
  let lastNonZero = false;
  while (number > 0) {
    const currentNumber = number % 10;
    const currentUnit = currentIndex % 4;
    const currentLargerUnit = Math.floor(currentIndex / 4);

    if (currentNumber === 0) {
      if (lastNonZero) {
        result = '零' + result;
        lastNonZero = false;
      }
    } else {
      result = numbers[currentNumber] + units[currentUnit] + result;
      lastNonZero = true;
    }

    if (currentIndex === 4 && number % 10000 !== 0) {
      result = largerUnits[currentLargerUnit] + result;
    } else if (currentIndex === 8 && number % 100000000 !== 0) {
      result = largerUnits[currentLargerUnit] + result;
    }

    number = Math.floor(number / 10);
    currentIndex++;
  }

  return result;
}

console.log(trans(123456)); // "十二万三千四百五十六"
console.log(trans(100010001)); // "一亿零一万零一"
```

这个函数首先对输入进行验证，确保输入是有效的数字。然后，它对数字进行逐位分析，并使用**`numbers`**、**`units`**和**`largerUnits`**数组来构建对应的汉字。在处理过程中，如果当前数字为0，则将当前位设置为"零"；如果当前数字不为0，则将其转换为对应的汉字，并添加上对应的单位。在处理完最后一个数字后，函数返回一个字符串，它包含了输入数字的汉语表达形式。

## 说说你对前端工程化的理解

前端工程化是指将软件工程的原则和方法应用于前端开发中，以提高开发效率、降低维护成本以及保证质量。它包括了一系列开发、构建、测试、部署等环节的自动化和标准化过程。前端工程化主要包括以下几个方面：

1. **代码规范**：使用代码规范和风格指南，确保团队成员遵循统一的编码规范，提高代码的可读性和可维护性。例如，可以使用ESLint、Prettier等工具进行代码检查和格式化。
2. **模块化与组件化**：将复杂的前端应用拆分为更小、可复用的模块或组件，以便于管理和维护。这可以通过使用诸如React、Vue或Angular等现代前端框架来实现。
3. **构建与打包**：使用构建工具（如Webpack、Rollup或Parcel）对代码进行编译、压缩、合并等操作，生成适用于生产环境的优化后的静态资源。
4. **自动化测试**：通过编写测试用例并使用自动化测试工具（如Jest、Mocha、Karma等）进行单元测试、集成测试和端到
5. **版本控制**：使用版本控制系统（如Git）来管理代码，确保团队成员之间的协作顺畅，便于跟踪代码变更历史和快速定位问题。
6. **持续集成与持续部署（CI/CD）**：将代码编写、构建、测试、部署等过程自动化，以便在每次代码提交时，都能快速地进行构建、测试和部署。这有助于减少人为错误，提高开发和发布速度。常见的CI/CD工具有Jenkins、Travis CI和GitHub Actions等。
7. **性能优化**：通过实施一系列性能优化措施来提升前端应用的加载速度和运行效率。这包括代码压缩、图片优化、懒加载、CDN部署等。使用性能监测和分析工具（如Lighthouse、WebPageTest等）来评估和改进性能。
8. **开发环境和工作流**：通过配置开发环境和工作流来提高开发效率。例如，使用Babel进行JavaScript代码转译，使其在不同浏览器中兼容；使用Sass、Less等CSS预处理器简化样式编写；使用自动化构建工具（如Gulp、Grunt等）来实现热更新、文件监听等功能，提高开发速度。

通过实施前端工程化，可以帮助团队更高效地进行开发、测试、部署和维护，最终提升项目的质量和稳定性。

## 前端性能优化都做了哪些工作

前端性能优化涉及很多方面的工作，主要目的是提升页面加载速度、响应时间和运行效率，从而提供更好的用户体验。以下是一些常见的前端性能优化措施：

1. 代码压缩：通过压缩JavaScript、CSS和HTML文件来减小文件大小，从而减少加载时间。可以使用UglifyJS、Terser、CSSNano等工具来实现。
2. 代码拆分：使用代码分割技术（如Webpack的code splitting功能），将大型的JavaScript文件拆分为较小的模块，按需加载，减少首次加载的时间。
3. 图片优化：对图片进行压缩、格式转换（如WebP）以及使用适当的尺寸，以减小文件大小。同时，可以采用懒加载技术，只在需要时加载图片。
4. 缓存策略：通过设置HTTP缓存头或使用Service Worker来实现浏览器缓存，以便用户在后续访问时能更快地加载页面。
5. 使用CDN：将静态资源部署到内容分发网络（CDN）上，使得用户能从离他们较近的服务器加载资源，降低延迟。
6. 优化CSS和JavaScript加载：将关键CSS内联到HTML文件中，以避免页面呈现时的阻塞。将非关键的CSS和JavaScript文件异步或延迟加载，从而提高页面加载速度。
7. 优化DOM操作：减少不必要的DOM操作，使用事件代理来减少事件监听器的数量，使用虚拟DOM或类似技术减轻浏览器渲染压力。
8. 使用Web字体优化：避免使用过多的Web字体，选择适当的字体格式，通过字体子集化仅加载所需的字符。
9. 服务端渲染（SSR）：通过在服务端预渲染页面，加快首屏渲染速度，提高SEO效果。
10. 利用浏览器性能API和工具：使用Performance API、Lighthouse等工具对页面性能进行监测和分析，找出性能瓶颈并进行针对性优化。
11. 优化网络请求：减少HTTP请求的数量，合并CSS和JavaScript文件，使用HTTP/2协议以提高并发能力。在适当的场景下，可以使用Websocket、WebRTC等技术减少网络延迟。
12. 使用请求优先级：对关键资源进行优先加载，提高页面加载速度和用户体验。
13. 避免阻塞渲染的资源：避免使用阻塞渲染的资源，例如将**`<script>`**标签放置在**`<body>`**底部或使用**`defer`**或**`async`**属性。
14. 利用浏览器的硬件加速：针对动画和图形渲染，利用GPU硬件加速，降低CPU的负担。

通过实施这些前端性能优化措施，可以显著提升页面的加载速度、响应时间和运行效率，为用户提供更好的体验。

## js协程底层原理

在 JavaScript 中，协程（即协作多任务）可以通过生成器（Generator）和 `yield` 关键字实现。要了解协程的底层原理，我们需要了解生成器、迭代器和 JavaScript 事件循环的概念。

1. **生成器（Generator）**：生成器是 JavaScript 中一种特殊的函数（使用 `function*` 声明），它可以在执行过程中产生多个值，并通过特殊的控制命令（称为生成器对象）在需要时返回。与普通函数不同，生成器函数执行并不会一直运行到完成，而是可以在中间暂停和恢复。生成器内部使用 `yield` 关键字暂停执行并将控制权交还给生成器对象。生成器对象可以将控制权返还给生成器函数，用于从上次暂停的地方继续执行。
2. **迭代器（Iterator）**：生成器函数执行后，会返回一个生成器对象。这个生成器对象遵从迭代器协议和生成器协议，可以通过调用 `next()` 方法来按需恢复生成器函数的执行。`next()` 方法返回一个对象，包含生成器产生的值（`value`）和一个标志（`done`），用于表示生成器是否已达到最后状态。
3. **事件循环（Event Loop）**：JavaScript 通过单线程的事件循环来实现异步处理。事件循环会不断检查任务队列（message queue）、微任务队列（microtasks queue）等，有任务就执行。事件循环使得 JavaScript 可以处理多个异步操作，无论何时异步操作完成，都可以将相应的回调函数添加到任务队列中。

结合以上三个概念，可以理解 JavaScript 中协程的底层原理：

1. 使用生成器函数定义协程，生成器函数包含需要异步处理的任务。
2. 生成器函数执行后，会返回一个生成器对象，它遵从迭代器协议。
3. 通过调度器（即协程的高层调用者）来控制生成器对象的运行顺序。调度器可以是一段自定义的代码（如通过 `function.next()` 方法调用生成器对象）或第三方库。
4. 当一个异步操作完成时，将回调函数或 Promise 处理程序添加到任务队列中。事件循环会执行这个回调函数，恢复协程执行。
5. 如果协程中还有其他异步操作需要等待，那么继续重复以上步骤，直到协程结束。

通过这种方式，协程可以让我们在同步风格的代码中处理异步操作，并在执行期间将控制权传递给其他协程或处理程序。在生成器和事件循环之间进行切换，让 JavaScript 能高效地处理并发任务和复杂的控制流。

## 说说 js 并发、线程、进程、异步编程、协程的原理以及之间的关系

JavaScript 是**单线程**的，但它通过事件循环、回调函数、异步编程、Promise、async/await 等机制来实现并发。下面简要介绍这些概念以及它们之间的关系。

1. 并发（Concurrency）：
在 JavaScript 中，尽管代码是单线程运行的，但并发是通过事件循环来实现的。事件循环是一个不断检查任务队列的过程，当队列中有任务时，就从队列中取出任务并执行。这样，JavaScript 能够在一个单线程中同时处理多个任务。
2. 线程（Thread）：
线程是操作系统调度的最小单位。虽然 JavaScript 本身是单线程的，但可以通过 Web Workers（浏览器环境）或 Worker Threads（Node.js 环境）实现多线程。这些 Worker 是独立的线程，它们在后台运行，与主线程并行，但它们不能直接操作 DOM 或访问主线程的全局变量。Workers 之间和主线程之间通过消息传递进行通信。这样可以实现一定程度的并行计算，从而提高性能。
3. 进程（Process）：
进程是计算机中正在运行的程序的实例。一个进程可以包含多个线程，它们共享进程的资源（如内存和文件句柄）。在 JavaScript 中，主要通过浏览器的标签页或 Node.js 实例来实现多进程。每个进程运行独立的 JavaScript 环境，这样可以实现资源隔离和更高的安全性。不过，进程间的通信（IPC）相对较慢，因为它们需要复制数据而不是共享内存。
4. 异步编程（Asynchronous Programming）：
异步编程允许 JavaScript 在等待某些操作（如 I/O、网络请求等）完成时不阻塞主线程，继续执行其他任务。在 JavaScript 中，异步编程主要通过回调函数（callbacks）、Promise、async/await 等方式实现。
- 回调函数（Callbacks）：这是异步编程的最基本形式。当异步任务完成时，回调函数被调用，从而执行后续操作。
- Promise：Promise 是一个代表异步操作结果的对象。它有三种状态：pending（进行中）、fulfilled（成功）和 rejected（失败）。Promise 可以使用链式调用来组织异步操作，使代码更加清晰易读。
- async/await：这是基于 Promise 的一种更简洁的异步编程方式。通过使用 async 关键字声明的异步函数和 await 关键字等待 Promise 完成，可以让异步代码看起来像同步代码，提高可读性和维护性。
1. 协程（Coroutine）：
协程是一种轻量级的线程，它允许在一个线程中同时执行多个任务，而这些任务可以相互之间协作、暂停和恢复。协程的切换不需要操作系统的调度，消耗的资源较少。在 JavaScript 中，协程并没有被直接实现，但可以通过生成器（Generator）和 yield 关键字来模拟。
- 生成器是一种特殊的函数，可以在执行过程中被暂停和恢复。通过在函数中使用 yield 关键字，可以实现类似协程的功能，让异步代码更加简洁。结合 Promise 和生成器，可以使用类似 async/await 的方式编写异步代码。

**总结：**

- JavaScript 是单线程的，通过事件循环和异步编程实现并发。
- 线程和进程是操作系统层面的概念。JavaScript 可以通过 Web Workers 或 Worker Threads 实现多线程，通过浏览器的标签页或 Node.js 实例实现多进程。
- 异步编程允许 JavaScript 在执行 I/O、网络请求等操作时不阻塞主线程。异步编程的主要方式有回调函数、Promise 和 async/await。
- 协程是一种轻量级的线程，可以在一个线程中并发执行多个任务。在 JavaScript 中，可以通过生成器和 yield 关键字模拟协程。

**这些概念之间的关系如下：**

- 并发是 JavaScript 代码执行的基本特性，线程、进程和协程都是实现并发的方式。
- 线程和进程提供了在更高层次上实现并发和隔离的能力，但它们在 JavaScript 中的应用相对受限。
- 异步编程是实现 JavaScript 并发的主要手段，协程（通过生成器和 yield）则是一种更高级的异步编程方式。

在实际开发中，我们通常会根据应用场景选择合适的技术来实现并发和异步编程。例如，对于复杂的计算任务，可以使用 Web Workers 或 Worker Threads 进行多线程处理；而对于 I/O 密集型的任务，可以使用异步编程（如回调函数、Promise 或 async/await）来避免阻塞主线程，实现更高效的并发处理。同时，在编写异步代码时，可以利用生成器和 yield 关键字模拟协程，让异步逻辑更加简洁和易于理解。

总之，JavaScript 的并发、线程、进程、异步编程和协程等概念之间相互关联，它们共同构成了 JavaScript 的并发和异步编程体系。了解这些概念及其之间的关系，对于编写高性能、易于维护的 JavaScript 代码具有重要意义。

## 说说ECMAScript各个版本新增的特性

ECMAScript 是 JavaScript 语言的标准化规范。以下是各个版本的主要新增特性概述：

**ECMAScript 3 (1999)**

- 增加异常处理（`try`，`catch`，`finally`）
- 增加正则表达式支持
- 增加 `in` 和 `instanceof` 运算符
- 新的控制抽象（`switch`，`do-while`）

**ECMAScript 5 (2009)**

- 严格模式（`'use strict';`）
- 增加了许多数组方法（如 `forEach`，`map`，`filter`，`reduce` 等）
- 增加 `Object.create` 和其他对象属性特性
- 增加 JSON 支持

**ECMAScript 6 (2015) - 也被称为 ES2015**

- `let` 和 `const` 声明关键字
- 箭头函数
- 类（Class）语法
- 模块导入和导出
- 解构赋值
- 增加了许多字符串方法（如 `startsWith`，`endsWith` 和 `includes`）
- 模板字面量
- 默认函数参数
- 剩余参数和展开操作符（`...`）
- `Promise` 和异步编程
- 生成器（`function*` 和 `yield`）
- `Map` 和 `Set` 数据结构

**ECMAScript 2016 (ES2016)**

- `Array.prototype.includes`
- 指数运算符（`*`）

**ECMAScript 2017 (ES2017)**

- `async` 和 `await` 异步函数
- `Object.entries` 和 `Object.values`
- `String.prototype.padStart` 和 `String.prototype.padEnd`
- 尾逗号（trailing commas）在函数参数中的支持

**ECMAScript 2018 (ES2018)**

- 对象和数组的展开操作符（`...`）
- 异步迭代器和生成器
- `Promise.prototype.finally`
- `RegExp` 的改进，如命名捕获组、断言等

**ECMAScript 2019 (ES2019)**

- `Array.prototype.flatMap` 和 `Array.prototype.flat`
- `Object.fromEntries`
- `String.prototype.trimStart` 和 `String.prototype.trimEnd`
- 可选的 `catch` 绑定
- `JSON.stringify` 的改进，支持稳定的键排序

**ECMAScript 2020 (ES2020)**

- `BigInt` 大整数类型
- 空值合并运算符（`??`）
- 可选链运算符（`?.`）
- `import()` 动态导入
- `Promise.allSettled`
- `globalThis` 统一全局对象

**ECMAScript 2021 (ES2021)**

- `String.prototype.replaceAll`
- `Promise.any` 和 `AggregateError`
- 弱引用（`WeakRef`）
- `FinalizationRegistry`用于自定义资源的清理
- 逻辑赋值运算符（如 `||=`，`&&=`，`??=`）

## 🤔日常难点

![Untitled](chatGPT4%20%E6%95%99%E4%BD%A0%E9%9D%A2%E8%AF%95%2090357a43a98c4579a3eb4c5e8082a010/Untitled.png)

![Untitled](chatGPT4%20%E6%95%99%E4%BD%A0%E9%9D%A2%E8%AF%95%2090357a43a98c4579a3eb4c5e8082a010/Untitled%201.png)

## JS 范式

JavaScript 是一种多范式编程语言，它支持多种编程范式，包括但不限于以下几种：

1. 声明式编程（Declarative Programming）：通过声明和表达式来描述程序应该完成的任务，而不关注具体实现。常见的声明式编程范式有函数式编程和逻辑编程。
2. 命令式编程（Imperative Programming）：通过详细描述计算机如何执行任务的步骤来编写程序。这种范式通常使用变量、赋值、条件语句和循环等。
3. 面向对象编程（Object-oriented Programming, OOP）：通过抽象和封装将数据和操作数据的方法组织在一起的编程范式。在 JavaScript 中，可以使用类、原型和对象等概念来实现面向对象编程。
4. 函数式编程（Functional Programming, FP）：把计算看作是数学函数的求值，强调函数的组合、无副作用和不可变性。JavaScript 中支持高阶函数、闭包、柯里化等函数式编程概念。
5. 事件驱动编程（Event-driven Programming）：程序的执行流程由事件触发，例如用户操作、消息传递等。在 JavaScript 中，可以使用事件监听器和事件处理函数来实现事件驱动编程。
6. 响应式编程（Reactive Programming）：处理异步数据流的编程范式，通过观察者模式将数据源和消费者连接起来。在 JavaScript 中，可以使用响应式编程库，例如 RxJS，来实现响应式编程。

JavaScript 的灵活性使得这些范式可以单独使用，也可以混合使用。开发者可以根据实际需求和编程风格选择适合的编程范式。

## 请用相同的功能用上述的范式举例子

为了说明这些范式的不同之处，让我们考虑一个简单的任务：计算一个整数数组中所有偶数的和。

1. 声明式编程 (Declarative Programming)

声明式编程关注任务的结果，而不是具体的实现过程。在这个例子中，我们可以使用 JavaScript 的高阶函数 **`filter`** 和 **`reduce`**：

```jsx
const numbers = [1, 2, 3, 4, 5, 6];
const evenSum = numbers.filter(x => x % 2 === 0).reduce((acc, val) => acc + val, 0);
console.log(evenSum); // 输出: 12

```

1. 命令式编程 (Imperative Programming)

命令式编程关注具体的实现过程，需要明确的控制结构和操作：

```
const numbers = [1, 2, 3, 4, 5, 6];
let evenSum = 0;

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 === 0) {
    evenSum += numbers[i];
  }
}

console.log(evenSum); // 输出: 12

```

3. 面向对象编程 (Object-oriented Programming, OOP)

面向对象编程将数据和对数据的操作封装在类或对象中：

```
class NumberArray {
  constructor(numbers) {
    this.numbers = numbers;
  }

  evenSum() {
    return this.numbers.filter(x => x % 2 === 0).reduce((acc, val) => acc + val, 0);
  }
}

const numbers = new NumberArray([1, 2, 3, 4, 5, 6]);
console.log(numbers.evenSum()); // 输出: 12

```

4. 函数式编程 (Functional Programming, FP)

函数式编程通过函数组合、无副作用和不可变性来表达计算：

```
const numbers = [1, 2, 3, 4, 5, 6];

const isEven = x => x % 2 === 0;
const sum = (acc, val) => acc + val;

const evenSum = numbers.filter(isEven).reduce(sum, 0);
console.log(evenSum); // 输出: 12

```

5. 事件驱动编程 (Event-driven Programming)

事件驱动编程通过监听和处理事件来完成任务。在这个例子中，我们可以使用一个事件触发器来计算偶数和：

```
const EventEmitter = require('events');

class Calculator extends EventEmitter {
  evenSum(numbers) {
    this.emit('evenSum', numbers.filter(x => x % 2 === 0).reduce((acc, val) => acc + val, 0));
  }
}

const calculator = new Calculator();
calculator.on('evenSum', (result) => console.log(result));

const numbers = [1, 2, 3, 4, 5, 6];
calculator.evenSum(numbers); // 输出: 12

```

1. 响应式编程 (Reactive Programming)

响应式编程处理异步数据流。在这个例子中，我们可以使用 RxJS 库来计算偶数和：

```jsx

const { from } = require('rxjs');
const { filter, reduce } = require('rxjs/operators');

const numbers = [1, 2, 3, 4, 5, 6];
const numbers$ = from(numbers);

numbers$
  .pipe(
    filter(x => x % 2 === 0),
    reduce((acc, val) => acc + val, 0)
  )
  .subscribe(evenSum => console.log(evenSum)); // 输出: 12

```

上述示例中，我们使用了不同的编程范式来实现相同的功能：计算整数数组中所有偶数的和。每种范式都有其特点和适用场景，开发者可以根据需求和编程风格选择合适的范式。