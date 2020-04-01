# Inheritance

function Person\(first, last, age, gender, interests\) { this.name = { first, last }; this.age = age; this.gender = gender; this.interests = interests; };

```text
Person.prototype.greeting = function() {
  alert('Hi! I\'m ' + this.name.first + '.');
};

function Teacher(first, last, age, gender, interests, subject) {
  Person.call(this, first, last, age, gender, interests);

  this.subject = subject;
}

// 至此，问题是，Teacher 的 prototype 属性中，只有一个 constructor，指向 Teacher 函数
// 我们需要 Teacher 的 prototype 中，包含想要继承的方法

Teacher.prototype = Object.create(Person.prototype);

Object.defineProperty(Teacher.prototype, 'constructor', { 
  value: Teacher, 
  enumerable: false, // so that it does not appear in 'for in' loop
  writable: true 
});

Teacher.prototype.greeting = function() {
  var prefix;

  if (this.gender === 'male' || this.gender === 'Male' || this.gender === 'm' || this.gender === 'M') {
    prefix = 'Mr.';
  } else if (this.gender === 'female' || this.gender === 'Female' || this.gender === 'f' || this.gender === 'F') {
    prefix = 'Mrs.';
  } else {
    prefix = 'Mx.';
  }

  alert('Hello. My name is ' + prefix + ' ' + this.name.last + ', and I teach ' + this.subject + '.');
};
```

[构造函数继承](untitled-3.md)

[类](JavaScript/Object/Inheritance/Untitled%201.md)

