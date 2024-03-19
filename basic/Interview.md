## Вопросы которые были недавно:

- Чем параллелизм отличается от асинхронности?
- Как работает индексация в SQL?
- Чем отличается mutex от nslock?
- Какие бы выбрали типы mutable или immutable для использования в приложении и почему?
- Как реализовано наследование в objc или swift? 

## Может быть полезно:

- Чем отличается weak от unowned? [https://cocoacasts.com/what-is-the-difference-between-weak-and-unowned-references-in-swift ]()
- Как реализованы слабые ссылки в Swift? [https://www.mikeash.com/pyblog/friday-qa-2017-09-22-swift-4-weak-references.html]()
- Сессия для более глубокого понимания reference и value-типов в Swift [https://developer.apple.com/videos/play/wwdc2016/416/ ]() 
- Swift Method Dispatch [https://www.rightpoint.com/rplabs/switch-method-dispatch-table]()
- Чем async/await лучше GCD - [https://habr.com/ru/articles/727788/]()
- Задачки на алгоритмы и структуры данных - [https://www.hackerrank.com/interview/interview-preparation-kit?h_l=domains&h_r=hrw&utm_source=hrwCandidateFeedback]()

##  Многопоточность:

### Что выведется в консоль?
    NSObject *object = [NSObject new];
    dispatch_async(dispatch_get_main_queue(), ^
    {
        NSLog(@"A %d", [object retainCount]);
        dispatch_async(dispatch_get_main_queue(), ^
        {
            NSLog(@"B %d", [object retainCount]);
        });
        NSLog(@"C %d", [object retainCount]);
    });
    NSLog(@"D %d", [object retainCount]);

### Выведется ли в дебагер «Hello world»? Почему?

	- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
	{
	    dispatch_sync(dispatch_get_main_queue(), ^{
	        NSLog(@"Hello world");
	    });
	
	   /* Another implementation */
	   return YES;
	}