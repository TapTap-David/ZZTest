Nimble中的匹配函数
# 等值判断    
使用equal函数
expect(actual).to(equal(expected))
expect(actual) == expected
expect(actual) != expected

# 是否是同一个对象
使用beIdenticalTo函数
expect(actual).to(beIdenticalTo(expected))
expect(actual) === expected
expect(actual) !== expected

# 比较    
expect(actual).to(beLessThan(expected))
expect(actual) < expected
expect(actual).to(beLessThanOrEqualTo(expected))
expect(actual) <= expected
expect(actual).to(beGreaterThan(expected))
expect(actual) > expected
expect(actual).to(beGreaterThanOrEqualTo(expected)) expect(actual) >= expected

# 比较浮点数    
expect(10.01).to(beCloseTo(10, within: 0.1))

# 类型检查
expect(instance).to(beAnInstanceOf(aClass)) 
expect(instance).to(beAKindOf(aClass))

# 是否为真
// Passes if actual is not nil, true, or an object with a boolean value of true:
expect(actual).to(beTruthy())

// Passes if actual is only true (not nil or an object conforming to BooleanType true):
expect(actual).to(beTrue())

// Passes if actual is nil, false, or an object with a boolean value of false:
expect(actual).to(beFalsy())

// Passes if actual is only false (not nil or an object conforming to BooleanType false):
expect(actual).to(beFalse())

// Passes if actual is nil:
expect(actual).to(beNil())

# 是否有异常
// Passes if actual, when evaluated, raises an exception: 
expect(actual).to(raiseException())

// Passes if actual raises an exception with the given name:
expect(actual).to(raiseException(named: name))

// Passes if actual raises an exception with the given name and reason:
expect(actual).to(raiseException(named: name, reason: reason))

// Passes if actual raises an exception and it passes expectations in the block
// (in this case, if name begins with 'a r')

expect { exception.raise() }.to(raiseException { (exception: NSException) in
     expect(exception.name).to(beginWith("a r"))

})

# 集合关系
// Passes if all of the expected values are members of actual:
expect(actual).to(contain(expected...))

expect(["whale", "dolphin", "starfish"]).to(contain("dolphin", "starfish"))

// Passes if actual is an empty collection (it contains no elements):
expect(actual).to(beEmpty())

# 字符串
// Passes if actual contains substring expected:
expect(actual).to(contain(expected))

// Passes if actual begins with substring: 
expect(actual).to(beginWith(expected))
 
// Passes if actual ends with substring: 
expect(actual).to(endWith(expected))

// Passes if actual is an empty string, "": 
expect(actual).to(beEmpty())

// Passes if actual matches the regular expression defined in expected:
expect(actual).to(match(expected))

# 检查集合中的所有元素是否符合条件
// with a custom function:
expect([1,2,3,4]).to(allPass({$0 < 5}))

// with another matcher: 
expect([1,2,3,4]).to(allPass(beLessThan(5)))

# 检查集合个数
expect(actual).to(haveCount(expected))

# 匹配任意一种检查
// passes if actual is either less than 10 or greater than 20 
expect(actual).to(satisfyAnyOf(beLessThan(10), beGreaterThan(20)))

// can include any number of matchers -- the following will pass
expect(6).to(satisfyAnyOf(equal(2), equal(3), equal(4), equal(5), equal(6), equal(7)))

// in Swift you also have the option to use the || operator to achieve a similar function 
expect(82).to(beLessThan(50) || beGreaterThan(80))

this is first
