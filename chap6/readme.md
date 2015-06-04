# Chap6

## ���� ���
### object �� scala ���� �����ϴ�, singleton instance �� �����ϱ� ���� ����̴�.
```scala
object foo {
  def bar = {...}
}
```
### class �̸��� ������ object�� companion object �� �θ���.
```scala
#�ݵ�� ���� file �ȿ� class �� object �� ���ǵǾ� �־�� �Ѵ�.
class foo {}
object foo {}
```
### apply method�� ()�� overloading �� �� �ִ� Ư���� method �̴�.(1�� 8p)
```scala
class companion(val _Member :String) {
  println(_Member)
}

object companion {
  def apply(param :String) = new companion("<<"+param+">>")
}

object foo extends App {
  companion("Hello")
  new companion("777")
}
```
### apply method�� ��ʴ� ���� 2 �����̴�.
1. companion method �� factory
2. new keyword ������ ���� functional syntax �� oo syntax �� ����

### scala ���α׷��� entry point �� object ���� Array[String] => Unit ������ main method �̴�.
### main method ��� App trait �� ����� ���� �ִ�.
### enumeration type ��� enumeration class �� �����Ѵ�.

## ����Ǯ�� �ؼ�
1.
```scala
object Conversion {
  def inchesToCentimeters(param :Double) = {param * 2.54}
  def gallonsToLiters(param :Double) = {param * 3.78541178}
  def milesToKilometers(param :Double) = {param * 1.609344}
}
```

2.
```scala
abstract class UnitConversion {
  def convert(param :Double) :Double
}

object inch2CM extends UnitConversion {
  def convert(param :Double) :Double = {param *2.54}
}
...

//�Ǵ�
abstract class UnitConversion(val convertee :Double) {
  def convert(value :Double) :Double = {convertee * value}
}

object inch2CM extends UnitConversion(2.54)

```