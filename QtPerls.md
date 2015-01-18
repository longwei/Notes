Qt Perls




1. D-pointer
=====
It is for binary compatibility
for example
```code
class MyClass {
public:
  MyClass();
  ~MyClass();
private:
  int myVar;
};
```
if I change myVar to double, oops

```code
class MyClass {
public:
  MyClass();
  ~MyClass();
private:
  MyClassPrivate * const d_ptr;
  Q_DECLARE_PRIVATE(MyClass);
};

class MyClassPrivate
{
public:
  MyClassPrivate(MyClass *parent);
private:
  MyClass * const q_ptr;
  Q_DECLARE_PUBLIC(MyClass);
  int myVar;
};
```


Q_DECARE_PUBLIC and Q_DECLARE_PRIVATE are marco that expend to helper functions and friend two togather.

2. Meta Object
======
aka how is signal & slot works
first of all, Qt have reflection or meta object genereated my moc
as long as there is a Q_OBJECT, moc will scane through header and generate implementation of the signals, bookkeeping class informations.
that's why qobject_cast is preferred when conversing qobjects.

3.

4. Event loop
how to make sure thing happen before event loop happens?
timer





