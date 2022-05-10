<!-- 
This README describes the package. If you publish this package to pub.dev,
this README's contents appear on the landing page for your package.

For information about how to write a good package README, see the guide for
[writing package pages](https://dart.dev/guides/libraries/writing-package-pages). 

For general information about developing packages, see the Dart guide for
[creating packages](https://dart.dev/guides/libraries/create-library-packages)
and the Flutter guide for
[developing packages and plugins](https://flutter.dev/developing-packages). 

TODO: Put a short description of the package here that helps potential users
know whether this package might be useful for them.

## Features

TODO: List what your package can do. Maybe include images, gifs, or videos.

## Getting started

TODO: List prerequisites and provide or point to information on how to
start using the package.
-->

## Usage

```yaml
dependencies:
  flutter:
    sdk: flutter

  chart_view:
    git: https://github.com/EaniaHuui/selector_plus.git
```

```dart
import 'package:selector_plus/selector_plus.dart';
```

比如我们需要监听的对象是`UserModel`
```dart
SelectorPlus<UserController, UserModel>(
  selector: controller.data,
  builder: (context, value, child) {
    return Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          Text(
            "name: ${value?.name}",
          ),
          Text(
            "email: ${value?.email}",
          ),
        ],
      ),
    );
  },
)
```
修改数据，然后刷新UI
```dart
data.value?.name = 'Flutter';
data.update();
notifyListeners();
```
或者
```dart
data.value = UserModel(name: "Flutter", email: "123@xx.com");
notifyListeners();
```
当然，对数组类数据也进一步做了处理，具体使用如下：
```dart
SelectorListPlus<UserController, UserModel>(
  selector: controller.list,
  builder: (context, value, child) {
    return ListView.builder(
      itemCount: value.length,
      itemBuilder: (context, index) {
        final item = value[index];
        return ListTile(
          title: Text(item.name),
          subtitle: Text(item.email),
        );
      },
    );
  },
)
```
修改数据更新UI
```dart
list.value[index].name = 'Flutter';
list.update();
notifyListeners();
```
或者
```dart
list.value= [UserModel(name: "Flutter", email: "123@xxx.com")];
notifyListeners();
```
增加
```dart
list.add(UserModel(name: "Flutter", email: "123@xx.com"));
notifyListeners();
```
删除
```dart
list.remove(index);
notifyListeners();
```



<!-- 
## Additional information

TODO: Tell users more about the package: where to find more information, how to 
contribute to the package, how to file issues, what response they can expect 
from the package authors, and more.
-->
