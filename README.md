# Introduction
This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.

# Table of Contents
- [Styles and Conventions](#styles-and-conventions)
    - [Lazy programming](#Lazy-programming)
 


This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.This style guide describes the preferred style for code written as part of the Flutter project (the framework itself and all our sample code). Flutter application developers are welcome to follow this style as well, but this is by no means required. Flutter will work regardless of what style is used to author applications that use it.

# Lazy programming
   


# flutter_codding_style
Tài liệu tham khảo: https://github.com/flutter/flutter/wiki/Style-guide-for-Flutter-repo/5c279fe8d7b52d31ebcf05385f69c636a6b8e676#philosophy

# Quy tắt đặt tên biến
Bắt đầu tên biết toàn cục bằng "k"
Ví dụ:
```kotlin
const double kParagraphSpacing = 1.5;
const String kSaveButtonTitle = 'Save';
const Color _kBarrierColor = Colors.black54;
```

# Quy tắc đặt tên cho typedefs và biến hàm
Ví dụ:
```kotlin
typedef void LoggerOutputFunction(String msg);

class Logger {
  LoggerOutputFunction out;
  Logger() {
    out = print;
  }
  void log(String msg) {
    out(msg);
  }
}

void timestampLoggerOutputFunction(String msg) {
  String timeStamp = Date.now().toString();
  print('${timeStamp}: $msg');
}

void main() {
  Logger l = new Logger();
  l.log('Hello World');
  l.out = timestampLoggerOutputFunction;
  l.log('Hello World');
}
```
# Viết hoa các mã định danh phù hợp với chính tả
Ví dụ: 
tên biến, fuction
```kotlin
///biết
toolbar
appBar
tabBar
offStage

///hàm
caculateMonth

```

tên class
```kotlin
class Persion {
}

```

# Đánh vần các từ trong định danh và nhận xét một cách chính xác
Tránh cách viết "cute". Ví dụ: 'colors', không phải 'colorz'.
Thích cách viết tiếng Anh Mỹ. Ví dụ: 'colorize' chứ không phải 'colourise'.
Ưu tiên các từ ghép hơn cách viết "cute" để tránh xung đột với các từ dành riêng. Ví dụ: 'classIdentifier' chứ không phải 'klass'.

# Sử dụng setter, getter
Trừ khi điều này gây ra các vấn đề khác, hãy sử dụng giá trị cho tên đối số của phương thức setter, getter. Điều này giúp việc sao chép/dán bộ cài đặt sau này dễ dàng hơn.
Ví dụ:
```kotlin
class Persion {
  int _weight;
  set weight(int value) {
    assert(weight >= 0);
    _weight = value;
  }
  int get weight => _weight
}
```

# Xác định các biến và phương thức chỉ được sử dụng để debug
Không sử dụng debugging biến hoặc hàm (hoặc class) trong production code.

# Tránh đặt comment câu hỏi
Tìm câu trả lời cho câu hỏi hoặc mô tả sự nhầm lẫn, bao gồm cả tài liệu tham khảo về nơi tìm thấy câu trả lời.
Nếu nhận xét về cách giải quyết do lỗi, hãy để lại liên kết đến lỗi và TODO để dọn dẹp khi lỗi được sửa.
Ví dụ:
```kotlin
/ BAD:

// What should this be?

// This is a workaround.


// GOOD:

// According to this specification, this should be 2.0, but according to that
// specification, it should be 3.0. We split the difference and went with
// 2.5, because we didn't know what else to do.

// TODO(username): Converting color to RGB because class Color doesn't support
//                 hex yet. See http://link/to/a/bug/123
```

# Để lại mẩu bánh mì trong phần comment
```kotlin
// GOOD:

/// An object representing a sequence of recorded graphical operations.
///
/// To create a [Picture], use a [PictureRecorder].
///
/// A [Picture] can be placed in a [Scene] using a [SceneBuilder], via
/// the [SceneBuilder.addPicture] method. A [Picture] can also be
/// drawn into a [Canvas], using the [Canvas.drawPicture] method.
abstract class Picture ...
```

```kotlin
/// See also:
///
/// * [FooBar], which is another way to peel oranges.
/// * [Baz], which quuxes the wibble.
```

# Sử dụng /// cho tài liệu riêng tư chất lượng công cộng
Nói chung, mã riêng có thể và cũng nên được ghi lại. Nếu tài liệu đó có chất lượng đủ tốt để chúng tôi có thể đưa nó nguyên văn khi đặt lớp ở chế độ công khai (tức là nó đáp ứng tất cả các nguyên tắc về văn phong ở trên), thì bạn có thể sử dụng /// cho những tài liệu đó, mặc dù chúng là riêng tư. Tài liệu về các API riêng tư không đủ chất lượng chỉ nên sử dụng //. Bằng cách đó, nếu chúng tôi công khai lớp tương ứng, những nhận xét tài liệu đó sẽ bị gắn cờ là thiếu và chúng tôi sẽ biết cách kiểm tra chúng cẩn thận hơn. Hãy thoải mái thận trọng trong những gì bạn cho là "đủ chất lượng". Bạn có thể sử dụng // ngay cả khi bạn có nhiều đoạn tài liệu; đó là dấu hiệu cho thấy chúng ta nên xem xét lại tài liệu một cách cẩn thận khi công khai mã.

# Constructor syntax
```kotlin
// one-line constructor example
abstract class Foo extends StatelessWidget {
  Foo(this.bar, { Key key, this.child }) : super(key: key);
  final int bar;
  final Widget child;
  // ...
}

// fully expanded constructor example
abstract class Foo extends StatelessWidget {
  Foo(
    this.bar, {
    Key key,
    Widget childWidget,
  }) : child = childWidget,
       super(
         key: key,
       );
  final int bar;
  final Widget child;
  // ...
}
```

# Ưu tiên độ dài dòng 80 ký tự
```kotlin
// BAD
final int a = 1;
final int b = 2;
final int c =
    a.very.very.very.very.very.long.expression.that.returns.three.eventually().but.is.very.long();
final int d = 4;
final int e = 5;

// BETTER
final int a = 1;
final int b = 2;
final int c = a.very.very.very.very.very.long.expression.that.returns.three.eventually().but.is.very.long();
final int d = 4;
final int e = 5;
```

# Thụt lề danh sách đối số và tham số nhiều dòng bằng 2 ký tự
Ví dụ:
```kotlin
Foo f = Foo(
  bar: 1.0,
  quux: 2.0,
);
```

# Sử dụng ⇒ khi chỉ return về...
Ví dụ:
```kotlin
// GOOD, but slightly more verbose than necessary since it doesn't use =>
  @override
  Widget build(BuildContext context) {
    return PopupMenuButton<String>(
      onSelected: (String value) { print('Selected: $value'); },
      itemBuilder: (BuildContext context) {
        return <PopupMenuItem<String>>[
          PopupMenuItem<String>(
            value: 'Friends',
            child: MenuItemWithIcon(Icons.people, 'Friends', '5 new')
          ),
          PopupMenuItem<String>(
            value: 'Events',
            child: MenuItemWithIcon(Icons.event, 'Events', '12 upcoming')
          ),
        ];
      }
    );
  }

  // GOOD, does use =>, slightly briefer
  @override
  Widget build(BuildContext context) {
    return PopupMenuButton<String>(
      onSelected: (String value) { print('Selected: $value'); },
      itemBuilder: (BuildContext context) => <PopupMenuItem<String>>[
        PopupMenuItem<String>(
          value: 'Friends',
          child: MenuItemWithIcon(Icons.people, 'Friends', '5 new')
        ),
        PopupMenuItem<String>(
          value: 'Events',
          child: MenuItemWithIcon(Icons.event, 'Events', '12 upcoming')
        ),
      ]
    );
  }
```

# Sử dụng 'if' khỏi câu lệnh của nó
Không đặt phần câu lệnh của câu lệnh 'if' trên cùng một dòng với biểu thức, ngay cả khi nó ngắn. (Làm như vậy sẽ khiến bạn không thấy rõ rằng có mã liên quan ở đó. Điều này đặc biệt quan trọng đối với việc trả lại sớm.)
Ví dụ:
```kotlin
// BAD:
if (notReady) return;

// GOOD:
if (notReady)
  return;

// ALSO GOOD:
if (notReady) {
  return;
}
```

# Căn chỉnh biểu thức
Nếu có thể, các biểu thức con trên các dòng khác nhau phải được căn chỉnh để làm cho cấu trúc của biểu thức trở nên dễ dàng hơn. Khi thực hiện việc này với chuỗi câu lệnh return || hoặc toán tử &&, hãy cân nhắc đặt toán tử ở phía bên trái thay vì phía bên phải.

Ví dụ:
```kotlin
// BAD:
if (foo.foo.foo + bar.bar.bar * baz - foo.foo.foo * 2 +
    bar.bar.bar * 2 * baz > foo.foo.foo) {
  // ...
}

// GOOD (notice how it makes it obvious that this code can be simplified):
if (foo.foo.foo     + bar.bar.bar     * baz -
    foo.foo.foo * 2 + bar.bar.bar * 2 * baz   > foo.foo.foo) {
  // ...
}
// After simplification, it fits on one line anyway:
if (bar.bar.bar * 3 * baz > foo.foo.foo * 2) {
  // ...
}
```

```kotlin
// BAD:
return foo.x == x &&
    foo.y == y &&
    foo.z == z;

// GOOD:
return foo.x == x &&
       foo.y == y &&
       foo.z == z;

// ALSO GOOD:
return foo.x == x
    && foo.y == y
    && foo.z == z;
```

# Sử dụng asserts
```kotlin
abstract class RenderBox extends RenderObject {
  // ...

  double getDistanceToBaseline(TextBaseline baseline, {bool onlyReal: false}) {
    // simple asserts:
    assert(!needsLayout);
    assert(!_debugDoingBaseline);
    // more complicated asserts:
    assert(() {
      final RenderObject parent = this.parent;
      if (owner.debugDoingLayout)
        return (RenderObject.debugActiveLayout == parent) &&
            parent.debugDoingThisLayout;
      if (owner.debugDoingPaint)
        return ((RenderObject.debugActivePaint == parent) &&
                parent.debugDoingThisPaint) ||
            ((RenderObject.debugActivePaint == this) && debugDoingThisPaint);
      assert(parent == this.parent);
      return false;
    });
    // ...
    return 0.0;
  }

  // ...
}
```
