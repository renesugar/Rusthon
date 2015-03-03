Callback Functions/Methods
----------------

TODO fix `def __init__(self, x:f32=0.0, y:f32=0.0):` segfaults


```rusthon
#backend:c++

class Vec2:
	def __init__(self, x:f32, y:f32):
		self.x = x
		self.y = y

	def add(self, other:Vec2) ->Vec2:
		print 'ADD....'
		v = Vec2(self.x+other.x, self.y+other.y)
		return v

	def show(self):
		print self.x
		print self.y


def call_method( callback:lambda(Vec2)(Vec2), other:Vec2 ) ->Vec2:
	v = callback( other )
	return v


def main():
	v1 = Vec2( 1.0, 2.0 )
	v2 = Vec2( 100.0, 200.0 )
	v1.show()
	v2.show()
	print 'callback test...'
	v3 = call_method(
		lambda o=Vec2: v1.add(o), 
		v2 
	)
	v3.show()
	print 'ok'
```