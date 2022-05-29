## React Native

- 네이티브 앱 : 각 OS에서 적합한 프로그래밍 언어로 OS에 맞게 제작한 모바일 앱
    - ios : Objective-C, Swift
    - Android : 자바, 코틀린
- 하이브리드 웹앱 : 기존의 웹 기술 (HTML, CSS, javascript)을 사용하여 제작할 수 있는 앱
- 하이리드 앱 : 하이브리드 웹앱과 다르게 웹 쀼를 사용하지 않고 네이티브와 통신하는 방식의 앱 : 네이티브 스크립트, 플루터

1. 리액트 네이티브 장점
    
    1)  비용
    
    하나의 언어로 ios, 안드로이드용 앱을 동시에 개발할 수 있음
    
    버그가 발생해도 하나의 소스코드만 수정하면 해결됨, 유지보수 비용이 네이티브 앱 개발보다 적게 든다는 것
    
2. 리액트 네이티브 단점
    
    1) 성능문제
    
    2) 네이티브 기능 개발
    
    개발하는 앱 서비스가 특별한 네이티브 기능을 가지고 있어 오픈소스가 존재하지 않은 경우, ios와 안드로이드의 네이티브 부분을 개별적으로 개발해야 하는 문제가 발생한다. 이런 독특한 네이티브 기능을 많이 가지는 서비스라면, 리액트 네이티브 개발자, ios 개발자, 안드로이드 개발자가 필요하고 네이티브 앱으로 개발할 때보다 개발 리소스와 유지보수 비용이 더 발생한다.
    
    - SNS 혹은 단순한 서비스를 개발할 때에는 리액트 네이티브를 사용한다.
    - 인스타그램과 같이 SNS + 카메라 필터와 같이 특정 작업이 들어갈 때에는 리액트 네이티브와 함께 다른 기술을 병합해서 사용한다.
    - 하드웨어를 다루거나 혹은 디바이스를 커스터마이징 하는 작업이 필요한 앱이면, 네이티브 언어를 사용해서 Android, Ios를 각각 개발한다.


# 

```jsx
import { StatusBar } from 'expo-status-bar';
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
	return (
		<View style={styles.container}>
			<Text> Open up App.js to start working on your app ! </Text>
			<StatusBar style="auto" />
		</View>
	)
}

const styles = StyleSheet.create({
	container: {
		flex: 1,
		backgroundColor: '#fff',
		alignItems: 'center',
		justifyContent: 'center'
	},
});

```

- [ ]  <View>
- html에서 div태그와 같은 역할을 한다.
- [ ]  <Text>

- [ ]  <Button>
- 버튼 컴포넌트
- [ ]  <TouchableOpacity>
- 버튼과 같은 화면 터치기능
- [ ]  <SafeAreaView>
- 리액트 네이티브에서는 자동으로 padding값이 적용되어 아이폰 노치 디자인문제를 해결할 수 있는 컴포넌트 제공
- [ ]  <StatusBar>
- 리액트 네이티브에서 핸드폰 상태바를 제어할 수 있는 StatusBar컴포넌트를 제공
- [ ]  <TextInput>
- text input 태그로써의 기능을 한다.
- [ ]  Dimensions
- 리액트 네이티브에서는 크기가 다양한 모바일 기기에 대응하기 위해 현재 화면의 크기를 알 수 있는 `Dimensions`와 `useWindowDimensions`를 제공
- 두 기능 모두 현재 기기의 화면 크기를 알 수 있고, 이를 이용해 다양한 크기의 기기에 동일한 모습으로 적용될 수 있도록 코드를 작성할 수 있다.
    - `Dimensions` 처음 값을 받아왔을 때의 크기로 고정되기 때문에 기기를 회전해서 화면이 전환되면 변화된 화면의 크기와 일치하지 않을 수 있다. 이런 상황을 위해 이벤트 리스너를 등록하여 화면의 크기 변화에 대응할 수 있도록 제공하며 `useWindowDimensions` 를 리액트 네이트브에서 제공하는 Hooks 중 하나로, 화면의 크기가 변경되면 화면의 크기, 너비, 높이를 자동으로 업데이트한다.

```jsx
import { Dimensions } from 'react-native';

const StyledInput = styled.TextInput `
	width: ${({width}) => width-40}px;
`;

const Input = () => {
	const width = Dimensions.get('window').width;
	return <StyledInput width={width} />;
;

// useWindowDimensions를 사용한다면 다음과 같이 작성한다.
import { useWindowDimensions } from 'react-native';

const StyledInput = styled.TextInput `
	width: ${({width}) => width-40}px;
`;

const Input = () => {
	const width = useWindowDimensions().width;
	return <StyledInput width={width} />;
};
```

- [ ]  조건문 사용

JSX는 내부에서 if문을 사용할 수 있습니다만, if문을 즉시 실행함수 형태로 작성해야 한다.

```jsx
const name = 'Beomjun';
return (
	<View style={styles.container}>
	<Text style={styles.text}>
		{() => {
			if(name === 'hanbit') return 'My name is Hanbit';
			else if(name === 'Beomjun') return 'My name is Beomjun';
			else return 'My name is React Native';
		})()}
	</Text>
	<StatusBar style='auto' />
	</View>
);
}
...
```

- [ ]  삼항 연산자

JSX는 내부에서 if 조건문 외에도 삼항 연산자를 사용할 수 있다. App.js파일을 다음과 같이 수정해보겠습니다.

```jsx
export default function App() {

	const name = 'Beomjun';
	return (
		<View style={styles.container}>
			<Text styles={styles.text}>
				my name is {name === 'Beomjun' ? 'Beomjun Kim' : 'React Native'}
			</Text>
		</View>
	);
}
```

- [ ]  AND 연산자와 OR 연산자

이번에는 JSX에서 AND연산자와 OR연산자를 잘 이용하면 특정 조건에 따라 컴포넌트의 렌더링 여부를 결정하도록 코드를 구성할 수 있다.

```jsx
export default function App() {

	const name = 'Beomjun';
	return (
		<View style={styles.container}>
			{name === 'Beomjun' && (
				<Text style={styles.text}> My name is Beomjun</Text>
			)}
			{name === 'Beomjun' && (
				<Text style={styles.text}> My name is not Beomjun</Text>
			)}
			<StatusBar style="auto" />
		</View>
	);
}
...
```

- [ ]  내부 컴포넌트
- Button
- TouchableOpacity

```jsx
import React from 'react';
import { TouchableOpacity, Text } from 'react-native';

const MyButton = () => {
	return (
		<TouchableOpacity>
			<Text style={{ fontSize: 24 }}>My Button</Text>
		</TouchableOpacity>
	);
}
export default MyButton;
```

- [ ]  props와 state
- props란 properties를 줄인 표현으로, 부모 컴포넌트로 부터 전달된 속성값 혹은 상속받은 속성값을 말한다.
- 부모 컴포넌트가 자식 컴포넌트의 props를 설정하면 자식 컴포넌트에서는 해당 props를 사용할 수 있지만 변경하는 것은 불가능하다.

✔️ props 전달하고 사용하기

```jsx
const App = () => {
	return (
			<View>
				<MyButton title="Button" />
			</View>
	)
}

...
const MyButton = props => {
	console.log(props);
	return (

		<TouchableOpacity>
			<Text>{props.title}</Text>
		</TouchableOpacity>
	);
};

...

결과
Object {
	"title" : "Button"
}
```

- [ ]  defaultProps

만약 사용해야 하는 값이 props로 전달되지 않으면 어떻게 될까요? App 컴포넌트에서 아무값도 전달하지 않으면서 MyButton 컴포넌트를 사용해보겠다.

```jsx
const MyButton = props => {...};

MyButton.defaultProps = {
	title : 'Button'
};
export default MyButton;

//함수를 전달해서 버튼 클릭 시 전달된 함수가 호출
const MyButton = props => {
	return (
		<TouchableOpacity>
			<Text
				style={{...}}
				onPress={() => props.onPress()}
			></Text>
		</TouchableOpacity>
	)
```

- [ ]  state

props는 부모 컴포넌트에서 받은 값으로 변경할 수 없는 반면, state는 컴포넌트 내부에서 생성되고 값을 변경할 수 있으며 이를 이용해 컴포넌트 상태를 관리한다. 

- useState 사용하기

```jsx
const [state, setState] = useState(initialState);
```

useState는 상태를 관리하는 변수와 그 변수를 변경할 수 있는 세터함수를 배열로 반환한다. 상태 변수는 직접 변경하는 것이 아니라 useState함수에서 반환한 세터 함수를 이용해야 한다.

```jsx
import React, { useState } from 'react';
import { View, Text } from 'react-native';
import MyButton from './MyButton';

const Counter = () => {
	const [count, setCount] = useState(0);
	return (
		<View>
		 <Text>{count}</Text>
			<MyButton onPress{() => setCount(count + 1)} />
			<MyButton onPress{() => setCount(count - 1)} />
		</View>
	)
}

export default Counter;
```

useState함수를 이용해서 숫자의 상태를 관리할 count 변수와 상태를 변경할 수 있는 setCount세터함수를 만들고, count의 초깃값을 0으로 설정

여러 개의 useState

```jsx
const [count, setCount] = useState(0);
const [double, setDouble] = useState(0);

return (
		<MyButton 
			onPress={() => {
				setCount(count + 1);
				setDouble(count + 2)
			}}			
			/>
		)
```

- [ ]  이벤트
1. Press 이벤트
- onPressIn : 터치가 시작될 때 항상 호출
- onPressOut : 터치가 해제될 때 항상 호출
- onPress : 터치가 해체될 때 onPressOut 이후 호출
- onLongPress : 터치가 일정 시간 이상 지속되면 호출

화면을 버튼을 클릭하면 onPressIn → onPressOut → onPress 혹은 onPressIn → onLongPress → onPressOut 순으로 호출되는 것을 확인할 수 있다.

1. change 이벤트

change 이벤트는 값을 입력하는 TextInput 컴포넌트에서 많이 사용된다. TextInput 컴포넌트를 이용하여 변화하는 텍스트를 출력
      
 # 

```jsx
import { StatusBar } from 'expo-status-bar';
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
	return (
		<View style={styles.container}>
			<Text> Open up App.js to start working on your app ! </Text>
			<StatusBar style="auto" />
		</View>
	)
}

const styles = StyleSheet.create({
	container: {
		flex: 1,
		backgroundColor: '#fff',
		alignItems: 'center',
		justifyContent: 'center'
	},
});

```

- [ ]  <View>
- html에서 div태그와 같은 역할을 한다.
- [ ]  <Text>

- [ ]  <Button>
- 버튼 컴포넌트
- [ ]  <TouchableOpacity>
- 버튼과 같은 화면 터치기능
- [ ]  <SafeAreaView>
- 리액트 네이티브에서는 자동으로 padding값이 적용되어 아이폰 노치 디자인문제를 해결할 수 있는 컴포넌트 제공
- [ ]  <StatusBar>
- 리액트 네이티브에서 핸드폰 상태바를 제어할 수 있는 StatusBar컴포넌트를 제공
- [ ]  <TextInput>
- text input 태그로써의 기능을 한다.
- [ ]  Dimensions
- 리액트 네이티브에서는 크기가 다양한 모바일 기기에 대응하기 위해 현재 화면의 크기를 알 수 있는 `Dimensions`와 `useWindowDimensions`를 제공
- 두 기능 모두 현재 기기의 화면 크기를 알 수 있고, 이를 이용해 다양한 크기의 기기에 동일한 모습으로 적용될 수 있도록 코드를 작성할 수 있다.
    - `Dimensions` 처음 값을 받아왔을 때의 크기로 고정되기 때문에 기기를 회전해서 화면이 전환되면 변화된 화면의 크기와 일치하지 않을 수 있다. 이런 상황을 위해 이벤트 리스너를 등록하여 화면의 크기 변화에 대응할 수 있도록 제공하며 `useWindowDimensions` 를 리액트 네이트브에서 제공하는 Hooks 중 하나로, 화면의 크기가 변경되면 화면의 크기, 너비, 높이를 자동으로 업데이트한다.

```jsx
import { Dimensions } from 'react-native';

const StyledInput = styled.TextInput `
	width: ${({width}) => width-40}px;
`;

const Input = () => {
	const width = Dimensions.get('window').width;
	return <StyledInput width={width} />;
;

// useWindowDimensions를 사용한다면 다음과 같이 작성한다.
import { useWindowDimensions } from 'react-native';

const StyledInput = styled.TextInput `
	width: ${({width}) => width-40}px;
`;

const Input = () => {
	const width = useWindowDimensions().width;
	return <StyledInput width={width} />;
};
```

- [ ]  조건문 사용

JSX는 내부에서 if문을 사용할 수 있습니다만, if문을 즉시 실행함수 형태로 작성해야 한다.

```jsx
const name = 'Beomjun';
return (
	<View style={styles.container}>
	<Text style={styles.text}>
		{() => {
			if(name === 'hanbit') return 'My name is Hanbit';
			else if(name === 'Beomjun') return 'My name is Beomjun';
			else return 'My name is React Native';
		})()}
	</Text>
	<StatusBar style='auto' />
	</View>
);
}
...
```

- [ ]  삼항 연산자

JSX는 내부에서 if 조건문 외에도 삼항 연산자를 사용할 수 있다. App.js파일을 다음과 같이 수정해보겠습니다.

```jsx
export default function App() {

	const name = 'Beomjun';
	return (
		<View style={styles.container}>
			<Text styles={styles.text}>
				my name is {name === 'Beomjun' ? 'Beomjun Kim' : 'React Native'}
			</Text>
		</View>
	);
}
```

- [ ]  AND 연산자와 OR 연산자

이번에는 JSX에서 AND연산자와 OR연산자를 잘 이용하면 특정 조건에 따라 컴포넌트의 렌더링 여부를 결정하도록 코드를 구성할 수 있다.

```jsx
export default function App() {

	const name = 'Beomjun';
	return (
		<View style={styles.container}>
			{name === 'Beomjun' && (
				<Text style={styles.text}> My name is Beomjun</Text>
			)}
			{name === 'Beomjun' && (
				<Text style={styles.text}> My name is not Beomjun</Text>
			)}
			<StatusBar style="auto" />
		</View>
	);
}
...
```

- [ ]  내부 컴포넌트
- Button
- TouchableOpacity

```jsx
import React from 'react';
import { TouchableOpacity, Text } from 'react-native';

const MyButton = () => {
	return (
		<TouchableOpacity>
			<Text style={{ fontSize: 24 }}>My Button</Text>
		</TouchableOpacity>
	);
}
export default MyButton;
```

- [ ]  props와 state
- props란 properties를 줄인 표현으로, 부모 컴포넌트로 부터 전달된 속성값 혹은 상속받은 속성값을 말한다.
- 부모 컴포넌트가 자식 컴포넌트의 props를 설정하면 자식 컴포넌트에서는 해당 props를 사용할 수 있지만 변경하는 것은 불가능하다.

✔️ props 전달하고 사용하기

```jsx
const App = () => {
	return (
			<View>
				<MyButton title="Button" />
			</View>
	)
}

...
const MyButton = props => {
	console.log(props);
	return (

		<TouchableOpacity>
			<Text>{props.title}</Text>
		</TouchableOpacity>
	);
};

...

결과
Object {
	"title" : "Button"
}
```

- [ ]  defaultProps

만약 사용해야 하는 값이 props로 전달되지 않으면 어떻게 될까요? App 컴포넌트에서 아무값도 전달하지 않으면서 MyButton 컴포넌트를 사용해보겠다.

```jsx
const MyButton = props => {...};

MyButton.defaultProps = {
	title : 'Button'
};
export default MyButton;

//함수를 전달해서 버튼 클릭 시 전달된 함수가 호출
const MyButton = props => {
	return (
		<TouchableOpacity>
			<Text
				style={{...}}
				onPress={() => props.onPress()}
			></Text>
		</TouchableOpacity>
	)
```

- [ ]  state

props는 부모 컴포넌트에서 받은 값으로 변경할 수 없는 반면, state는 컴포넌트 내부에서 생성되고 값을 변경할 수 있으며 이를 이용해 컴포넌트 상태를 관리한다. 

- useState 사용하기

```jsx
const [state, setState] = useState(initialState);
```

useState는 상태를 관리하는 변수와 그 변수를 변경할 수 있는 세터함수를 배열로 반환한다. 상태 변수는 직접 변경하는 것이 아니라 useState함수에서 반환한 세터 함수를 이용해야 한다.

```jsx
import React, { useState } from 'react';
import { View, Text } from 'react-native';
import MyButton from './MyButton';

const Counter = () => {
	const [count, setCount] = useState(0);
	return (
		<View>
		 <Text>{count}</Text>
			<MyButton onPress{() => setCount(count + 1)} />
			<MyButton onPress{() => setCount(count - 1)} />
		</View>
	)
}

export default Counter;
```

useState함수를 이용해서 숫자의 상태를 관리할 count 변수와 상태를 변경할 수 있는 setCount세터함수를 만들고, count의 초깃값을 0으로 설정

여러 개의 useState

```jsx
const [count, setCount] = useState(0);
const [double, setDouble] = useState(0);

return (
		<MyButton 
			onPress={() => {
				setCount(count + 1);
				setDouble(count + 2)
			}}			
			/>
		)
```

- [ ]  이벤트
1. Press 이벤트
- onPressIn : 터치가 시작될 때 항상 호출
- onPressOut : 터치가 해제될 때 항상 호출
- onPress : 터치가 해체될 때 onPressOut 이후 호출
- onLongPress : 터치가 일정 시간 이상 지속되면 호출

화면을 버튼을 클릭하면 onPressIn → onPressOut → onPress 혹은 onPressIn → onLongPress → onPressOut 순으로 호출되는 것을 확인할 수 있다.

1. change 이벤트

change 이벤트는 값을 입력하는 TextInput 컴포넌트에서 많이 사용된다. TextInput 컴포넌트를 이용하여 변화하는 텍스트를 출력
      
 https://sansanji.tistory.com/entry/React-Native-%EA%B0%9C%EB%B0%9C%EC%8B%9C-Native-%EA%B8%B0%EB%8A%A5-%EA%B0%9C%EB%B0%9C%ED%9B%84-%EC%97%B0%EA%B2%B0-%EB%B0%A9%EB%B2%95-%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C
