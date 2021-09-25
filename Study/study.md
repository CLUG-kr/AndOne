# 📢 (1주차) 스터디 일지

> ## 작성자 : 신지수
>
> ## 작성 날짜 : 2021.09.25
>
> ## 참여자 : 곽희준 신지수 이수은 한종욱

## ✅ 이번주 공부 내용 : 레이아웃 만들기

### ▶️ 제약 레이아웃

- 프로젝트를 생성하면 자동으로 만들어진다
- 제약조건을 이용해 그 안에 추가된 뷰들치를 결정
- 제약조건은 연결선으로 만들 수 있다
- 연결선은 뷰의 연결점을 다른 뷰나 레이아웃과 연결하여 만들 수 있다
- 연결선은 뷰가 어디에 위치할 지 알 수 있도록 연결하는 것이 중요하다
  
### ▶️ 리니어 레이아웃

- oirentation: 리니어 레이아웃에서 방향을 결정하는 속성.
- layout_gravity: 리니어 레이아웃 안에 있는 뷰를 정렬하는 속성.
- gravity: 뷰 안에 있는 내용물을 정렬하는 속성.
- layout_margin: 레이아웃의 테두리로 부터 뷰의 테두리를 얼만큼 띄울 지 정하는 속성. 상하좌우 모두 가능.
- padding: 뷰의 내용물을 뷰의 테두리와 얼마나 띄울지 정하는 속성.
- layout_weight: 여유 공간에서 뷰의 공간을 분할하는 속성. 비례식이랑 유사.
  
'''xml
<Button
        android:id="@+id/button4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_weight="3"
        android:text="Button" />
'''
  
### ▶️ 상대 레이아웃

- 부모 레이아웃이나 다른 뷰들의 상대적 위치를 이용해 배치하는 레이어.
- 제약 레이어와 유사.
- 실습했던 내용 중, 가운데 있는 버튼의 코드
  
'''xml
<Button
        android:id="@+id/button4"
        android:layout_width="match_parent"
        android:layout_height="606dp"
        android:layout_above="@+id/button5"
        android:layout_below="@+id/button3"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginStart="0dp"
        android:layout_marginTop="48dp"
        android:layout_marginBottom="16dp"
        android:text="Button" />
'''
  
### ▶️ 프레임 레이아웃

- 한 번에 하나의 뷰만 보여주는 레이아웃
- 주로 여러개의 뷰를 중첩시킬 때 사용함
- visibility: 뷰를 보여주는 속성. 보이고 싶은 땐 visible, 보여주고 싶지 않을 땐 invisible이나 gone을 사용
- 이런 속성을 이용해 특정 조건에 따라 볼 수 있는 뷰를 바꿀 수 있음. (e.g. 버튼을 누르면 이미지가 바뀜)
- mainactivity.java 코드. 클릭했을 때 이미지 변화하는 코드.
  
'''java
public class MainActivity extends AppCompatActivity {
    ImageView imageView;
    ImageView imageView2;

    int index = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = (ImageView) findViewById(R.id.imageView);
        imageView2 = (ImageView) findViewById(R.id.imageView2);
    }

    public void onButton1Clicked(View v){
        index += 1;
        if (index>1){
            index = 0;
        }

        if (index==0){
            imageView.setVisibility(View.VISIBLE);
            imageView2.setVisibility(View.INVISIBLE);
        } else if(index ==1){
            imageView.setVisibility(View.INVISIBLE);
            imageView2.setVisibility(View.VISIBLE);
        }

    }
}
'''
  
### ▶️ 드로어블 만들기

- 코드나 xml 파일로 그래픽을 만들 수 있는데 그것을 드로어블이라고 함
- 드로어블의 종류: 비트맵 드로어블, 상태 드로어블, 전환 드로어블, 쉐이프 드로어블
- 비트맵 드로어블: 이미지 파일을 보여줄 때 사용. 비트맵 이미지를 드로어블로 변경 가능. 그 반대도 가능
- 전환 드로어블: 두 개의 드로어블 간에 바뀌도록 만들 수 있음
- 상태 드로어블: 뷰의 상태에 따라 뷰에 보여줄 그래픽을 다르게 지정할 수 있음. state_press(눌린 상태), state_focused(포커스를 받은 상태) 등 state_로 시작하는 속성을 이용해 만들 수 있다.
-쉐이프 드로어블: XML로 도형을 그릴 수 있음. 최상위 태그를 shape로 지정하면 도형 하나를 지정할 수 있다. stroke(테두리 속성), width(두께 속성), color(색상 속성), solid(도형 안을 채우는 색상 속성), gradient(그라데이션을 줄 수 있는 태그)
- layer_list: 여러개의 item 태그가 들어갈 수 있는 태그. 이를 이용하여 여러 그래픽을 하나의 xml에 넣을 수 있다.  
- 쉐이프 드로어블 중 그라데이션 넣는 실습 코드

'''xml
<shape
    xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:startColor="#7288DB"
        android:centerColor="#3250B4"
        android:endColor="#254095"
        android:angle="90"
        android:centerY="0.5"
        />

    <corners android:radius="2dp" />
</shape>
'''

## 👊 Git (공부한 소스코드 공유)

| 작성자 |           주소            |
| :----: | :-----------------------: |
| 신지수 | 'https://github.com/CLUG-kr/AndOne.git' |
