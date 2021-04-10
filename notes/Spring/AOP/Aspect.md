# Aspect

## AOP

- 通知(Advice)

​	AspectJ提供了五种定义通知的注解：

| 注解            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| @Before         | 前置通知，在调用目标方法之前执行通知定义的任务               |
| @After          | 后置通知，在目标方法执行结束后，无论执行结果如何都执行通知定义的任务 |
| @AfterReturning | 后置通知，在目标方法执行结束后，如果执行成功，则执行通知定义的任务 |
| @AfterThrowing  | 异常通知，如果目标方法执行过程中抛出异常，则执行通知定义的任务 |
| @Around         | 环绕通知，在目标方法执行前和执行后，都需要执行通知定义的任务 |
| @Poincut        | 切面中的切入点                                               |
| @Aspect         | Aspect提供的标注切面类的注解                                 |

- 连接点(JoinPoint)

  就是spring中允许使用通知的地方，基本上每个方法前后抛异常时都可以是连接点

- 切点(Poincut)

  其实就是筛选出的连接点，一个类中的所有方法都是连接点，但又不全需要，会筛选出某些作为连接点做为切点。如果说通知定义了切面的动作或者执行时机的话，切点则定义了执行的地点

- 切面(Aspect)

  其实就是通知和切点的结合，通知和切点共同定义了切面的全部内容，它是干什么的，什么时候在哪执行

- 引入(Introduction)

  在不改变一个现有类代码的情况下，为该类添加属性和方法,可以在无需修改现有类的前提下，让它们具有新的行为和状态。其实就是把切面（也就是新方法属性：通知定义的）用到目标类中去

- 目标(target)

  被通知的对象。也就是需要加入额外代码的对象，也就是真正的业务逻辑被组织织入切面。

- 织入(Weaving)

  把切面加入程序代码的过程。切面在指定的连接点被织入到目标对象中，在目标对象的生命周期里有多个点可以进行织入：

  - 编译期：切面在目标类编译时被织入，这种方式需要特殊的编译器
  - 类加载期：切面在目标类加载到JVM时被织入，这种方式需要特殊的类加载器，它可以在目标类被引入应用之前增强该目标类的字节码
  - 运行期：切面在应用运行的某个时刻被织入，一般情况下，在织入切面时，AOP容器会为目标对象动态创建一个代理对象，Spring AOP就是以这种方式织入切面的。

## 切入点指示符

Spring AOP支持以下在切入点表达式中使用的AspectJ切入点指示符（PCD）：

- `execution`：用于匹配方法执行的连接点。这是在使用Spring AOP时要使用的主要切入点指示符。
- `within`：将匹配限制为某些类型内的连接点（使用Spring AOP时，在匹配类型内声明的方法的执行）。
- `this`：在bean引用（Spring AOP代理）是给定类型的实例的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。
- `target`：在目标对象（代理的应用程序对象）是给定类型的实例的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。
- `args`：将匹配限制为连接点（使用Spring AOP时方法的执行），其中参数是给定类型的实例。
- `@target`：在执行对象的类具有给定类型的注释的情况下，将匹配限制为连接点（使用Spring AOP时方法的执行）。
- `@args`：限制匹配的连接点（使用Spring AOP时方法的执行），其中传递的实际参数的运行时类型具有给定类型的注释。
- `@within`：将匹配限制为具有给定注释的类型内的连接点（使用Spring AOP时，使用给定注释的类型中声明的方法的执行）。
- `@annotation`：将匹配限制在连接点的主题（在Spring AOP中运行的方法）具有给定注释的连接点处。

## 表达式

​	在Spring AOP中，使用AspectJ的切点表达式语言定义切点其中excecution()是最重要的描述符，其它描述符用于辅助excecution()。

excecution()的语法如下：

```tex
execution(modifiers-pattern? ret-type-pattern declaring-type-pattern? name-pattern(param-pattern)throws-pattern?)
```

- modifier-pattern：表示方法的修饰符
- ret-type-pattern：表示方法的返回值
- declaring-type-pattern?：表示方法所在的类的路径
- name-pattern：表示方法名
- param-pattern：表示方法的参数
- throws-pattern：表示方法抛出的异常

## ProceedingJoinPoint

​	任何通知方法都可以将类型的参数声明为它的第一个参数 `org.aspectj.lang.JoinPoint`（请注意，在`@Around`需要声明类型的第一个参数`ProceedingJoinPoint`，它是`JoinPoint`的子类。该`JoinPoint`接口提供了许多有用的方法：

- `getArgs()`：返回方法参数。
- `getThis()`：返回代理对象。
- `getTarget()`：返回目标对象。
- `getSignature()`：返回建议使用的方法的描述。
- `toString()`：打印有关所建议方法的有用描述。