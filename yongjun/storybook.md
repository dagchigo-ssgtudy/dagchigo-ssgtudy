# Storybook

## 컴포넌트 란?

- 컴포넌트(Component)란 프로그래밍에 있어 재사용이 가능한 각각의 독립된 모듈
- 상호 교환 가능하고 표준화 된 UI 구성 요소입니다. UI 조각의 모양, 기능을 캡슐화합니다.
(ex: lego)

##  컴포넌트 주도 개발 - Component-Driven Development(CDD)

- 컴포넌트를 모듈 단위로 개발하여 사용자 인터페이스(UI) 구축에 도달하는 개발 및 설계 방법론
- 컴포넌트 수준에서 시작해 페이지나 화면 수준에서 끝나는 것으로 "바닥부터 끝까지"(bottom up) UI를 구축하는 과정

<img width="499" alt="스크린샷 2022-01-23 오후 1 28 10" src="https://user-images.githubusercontent.com/80729831/167231413-2832570e-b465-4123-bf24-1207ca8bcfd8.png">

## 컴포넌트 주도 개발의 장점

- 디자인 체계화
- 디자이너와 효율적인 협업
- 다른 프로젝트, 페이지에서도 쉽게 쓰고 공유 가능
- UI 단위 테스트가 가능

## 컴포넌트 익스플로러

- 컴포넌트 익스플로러는 앱의 컴포넌트를 다양한 테스트 "상태"에서 보여주는 별도의 응용 프로그램
- 익스플로러를 사용하여 컴포넌트에 중요한 상태로 정의된 모든 상태에 대해서 컴포넌트 테스트 가능
- [다양한 컴포넌트 익스플로러 보기](https://www.chromatic.com/blog/ui-component-explorers---your-new-favorite-tool/?source=post_page-----ce1109d56c8e----------------------)


## storybook
<img width="167" alt="스크린샷 2022-01-22 오후 2 37 34" src="https://user-images.githubusercontent.com/80729831/167231593-44b0f304-b729-40f7-889b-ed0e42cb8dd9.png">

- Storybook은 UI 구성 요소와 페이지를 별도로 구축하기 위한 오픈 소스 도구입니다. UI 개발, 테스트 및 문서화를 간소화합니다.
```jsx
Storybook은 컴포넌트를 위한 UI 개발 환경입니다. 
이를 통해 UI 컴포넌트의 다양한 상태 시각화 또는 인터랙티브 스타일로 개발 할 수 있습니다. 
Storybook은 앱 외부에서 실행되므로, 앱 모듈 종속성에 대해 걱정하지 않고
UI 컴포넌트를 독립적인 환경에서 개발할 수 있습니다.
```

## storybook과 같은 UI 개발 도구를 왜 사용할까?

- **기본적으로 독립적인 개발환경에서 실행**된다.
    - 애플리케이션의 다양한 상황에 구애받지 않고 UI컴포넌트를 집중적으로 개발 가능
- **테스트 및 개발 속도를 향상**시키는 장점
    - 자동으로 컴포넌트를 시각화하여 시뮬레이션할 수 있는 **다양한 테스트 상태를 확인 가능**
    - **UI 단위 테스트**, 즉 화면 크기 단위로 시각테스트를 해볼 수 있다
    - 재사용성을 확대하기 위해 컴포넌트를 **문서화 가능**
- 단순히 회사의 UI 라이브러리를 내부 개발자들을 위해 문서화(documentation)하기 위해서 사용할 수 있고, 외부 공개용 디자인 시스템(Design System)을 개발하기 위한 기본 플랫폼으로도 사용할 수 있다.

- **여러 프레임워크를 지원한다.** 스토리북은 처음에 리액트 스토리북으로 시작했지만, 현재는 리액트 네이티브, 뷰, 앵귤러, Ember, Riot 등 대부분의 프레임워크를 지원한다. 지원하는 프레임워크마다 별도의 npm 모듈을 제공하고 있기 때문에, 스토리북을 사용하기 위해서는 프로젝트 환경에 맞는 npm 모듈을 설치해야 한다.

<img width="300" alt="스크린샷 2022-01-23 오후 1 12 21" src="https://user-images.githubusercontent.com/80729831/167231578-5de36e0d-a172-47aa-bd7d-f23624d72f5a.png">

- **추가기능:** **addons**
  - addon 은 스토리북의 고급 기능과 새로운 워크플로우를 제공한다. (코드 예시로 설명)
  - UI와 동작을 확장


## 작동 방식

- 스토리북(Storybook)을 기본 구성 단위는 스토리(Story)
- 하나의 UI 컴포넌트는 보통 하나 이상의 Story를 가지게 됩니다.
- 각 Story는 해당 UI 컴포넌트가 어떻게 사용될 수 있는지를 보여주는 하나의 예시라고 생각하기
    - Storybook을 사용하면 UI 컴포넌트가 각각 독립적으로 어떻게 실제로 랜더링되는지 직접 시각적으로 테스트하면서 개발을 진행할 수 있다.

#### 0. 설치
  ```jsx
    npx sb init
  ```
  - 자동으로 .storybook 폴더가 생성되고, 그안에 config파일인 main.js, preview.js가 생긴다.

#### addons 설치
<img width="407" alt="스크린샷 2022-01-23 오후 3 22 53" src="https://user-images.githubusercontent.com/80729831/167232319-083c5443-99e9-4da7-8f31-6f6fb2ea7311.png">
https://www.npmjs.com/package/@storybook/addon-essentials
```jsx
npm install --save-dev @storybook/addon-essentials
```

```jsx
// .storybook/main.js

module.exports = {
  addons: ['@storybook/addon-essentials'],
};
```

```jsx
// .preview.js 
// 여기선 초기설정을 할 수 있음

export const parameters = {
  actions: { argTypesRegex: "^on[A-Z].*" },
  controls: {
    matchers: {
      color: /(background|color)$/i,
      date: /Date$/,
    },
  },
    backgrounds: {
      default: 'white',
      values: [
        {
          name: 'twitter',
          value: '#00aced',
        },
        {
          name: 'facebook',
          value: '#3b5998',
        },{
        name: 'white',
          value: '#fff',
        }
      ],
    },
    layout: 'fullscreen',
}
```

#### 2.컴포넌트 생성 + 3. props 정의

```jsx
// ~/components/Button.tsx
import React from 'react';
import './button.css';

interface ButtonProps {
  /**
   * Is this the principal call to action on the page?
   */
  primary?: boolean;
  /**
   * What background color to use
   */
  backgroundColor?: string;
  /**
   * How large should the button be?
   */
  size?: 'small' | 'medium' | 'large';
  /**
   * Button contents
   */
  label: string;
  /**
   * Optional click handler
   */
  onClick?: () => void;
}

/**
 * Primary UI component for user interaction
 */
export const Button = ({
  primary = false,
  size = 'medium',
  backgroundColor,
  label,
  ...props
}: ButtonProps) => {
  const mode = primary ? 'storybook-button--primary' : 'storybook-button--secondary';
  return (
    <button
      type="button"
      className={['storybook-button', `storybook-button--${size}`, mode].join(' ')}
      style={{ backgroundColor }}
      {...props}
    >
      {label}
    </button>
  );
};

```

```jsx
// ~/stories/Button.stories.tsx
import React from 'react';
import { ComponentStory, ComponentMeta } from '@storybook/react';

import { Button } from './Button';

export default {
  title: 'Example/Button',
  component: Button,
  argTypes: {
    backgroundColor: { control: 'color' },
  },
} as ComponentMeta<typeof Button>;

const Template: ComponentStory<typeof Button> = (args) => <Button {...args} />;

export const Primary = Template.bind({});
Primary.args = {
  primary: true,
  label: 'Button',
};

export const Secondary = Template.bind({});
Secondary.args = {
  label: 'Button',
};

export const Large = Template.bind({});
Large.args = {
  size: 'large',
  label: 'Button',
};

export const Small = Template.bind({});
Small.args = {
  size: 'small',
  label: 'Button',
};

```


#### 4. 구현하고자 하는 기능을 스토리로 작성
#### 5. 컴포넌트에서 기능 구현
#### 6. Storybook에서 잘 작동하는지 확인

컴포넌트, props, 스토리 작성이 완성되었다면, 5,6,7번 과정을 반복하며 컴포넌트를 완성해 가면 된다.

<br />
<br />

## 문서 작성 예시

- 타입을 지정해준 곳에 주석을 달아 docs- controls의 내용 추가
- 컴포넌트 선언해준 위에 컴포넌트의 내용 추가
- 컴포넌트에 대한 설명 작성은 1번 이미지
- 프롭스 설명 작성은 2번 이미지

<img width="300" alt="스크린샷 2022-05-07 오전 10 30 39" src="https://user-images.githubusercontent.com/80729831/167232646-8cfca973-5263-4f12-87ec-3202cc96767c.png">
<img width="300" alt="스크린샷 2022-05-07 오전 10 30 20" src="https://user-images.githubusercontent.com/80729831/167232649-4e23a217-fdbe-4f37-8211-e2ecdf9e8780.png">



## 사용시 고려할점

- 먼저 컴포넌트 단위로 많은 것을 고려하면서 개발을 하게되어 초기에 개발의 속도는 느려지고, 스토리북에 관련된 세팅과 이슈를 해결하는데 그만큼의 시간이 투입된다.
- 개인이 진행하는 작은 토이 프로젝트나 규모가 작은 프로젝트에서는 도입합으로서 얻는 이점이 별로 없다


<br />

 
#### addon knobs와 controls  
[https://url.kr/zughco](https://url.kr/zughco)
[https://www.npmjs.com/package/@storybook/addon-controls#installation](https://www.npmjs.com/package/@storybook/addon-controls#installation)

#### 참고하면 좋을 디자인 시스템
[https://ridi.design/](https://ridi.design/)
[https://dewberry9.github.io/future-of-design-system](https://dewberry9.github.io/future-of-design-system)
[https://url.kr/ov6cpq](https://url.kr/ov6cpq)


#### 참고 문서
[https://storybook.js.org/](https://storybook.js.org/)
[https://www.daleseo.com/storybook/](https://www.daleseo.com/storybook/)
[https://medium.com/@j_podracer/storybook의-유용함-8581ea618c32](https://medium.com/@j_podracer/storybook%EC%9D%98-%EC%9C%A0%EC%9A%A9%ED%95%A8-8581ea618c32)
[https://developer-adam.tistory.com/m/22](https://developer-adam.tistory.com/m/22)
[https://yamoo9.github.io/react-master/lecture/sb-cdd.html#cdd가-아닌-ui-개발](https://yamoo9.github.io/react-master/lecture/sb-cdd.html#cdd%E1%84%80%E1%85%A1-%E1%84%8B%E1%85%A1%E1%84%82%E1%85%B5%E1%86%AB-ui-%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF)
[https://meetup.toast.com/posts/178](https://meetup.toast.com/posts/178)
[https://url.kr/caqoxk](https://url.kr/caqoxk)
[https://www.howdy-mj.me/storybook/writing-stories/](https://www.howdy-mj.me/storybook/writing-stories/)
[https://velog.io/@yesdoing/번역-Component-Driven-Development-udjzqwqgay](https://velog.io/@yesdoing/%EB%B2%88%EC%97%AD-Component-Driven-Development-udjzqwqgay)
