# 📢 (2주차) 스터디 일지

> ## 작성자 : 이수은 
>
> ## 작성 날짜 : 2021.10.01
>
> ## 참여자 : 곽희준 신지수 이수은 한종욱

## ✅ 이번주 공부 내용 : 이벤트와 리스트뷰

### ▶️ 스크롤뷰 사용하기

1) 테이블 레이아웃

- 격자 모양으로 뷰를 배치할 때 사용
- 행 추가 가능
- 각각의 <TableRow> 안에는 여러 개의 뷰가 들어갈 수 있는 구조로 되어 있음

2) 스크롤뷰

- 글자나 이미지가 들어간 뷰가 화면 영역을 벗어나면 보이지 않게 됨
- 스크롤뷰로 이미지뷰/텍스트뷰 등을 감싸주기만 하면 스크롤뷰가 뷰의 영역을 계산하여 자동으로 스크롤 생성

'''xml
<ScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <TextView
                android:id="@+id/textView"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:textSize="50dp"
                android:text="안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n안녕하세요.\n" />
        </LinearLayout>
    </ScrollView>
'''

### ▶️ 이벤트 이해하기

1) 이벤트 처리 이해하기

- 이벤트의 종류는 다양 (터치 이벤트, 클릭 이벤트, 키 이벤트 등)
- 이벤트는 리스너를 이용하여 다룰 수 있음
- click -> touch event로 세분화 가능
- gesture event : touch event의 일정 패턴을 대신 계산해 줌 (ex 속도)
- event 발생시 토스트 메시지, 알림 대화상자, 간단한 애니메이션 등을 보여주게 만들 수 있음

'''java
View view = findViewById(R.id.view);
        view.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                int action = motionEvent.getAction();
                float curX = motionEvent.getX();
                float curY = motionEvent.getY();

                if (action == MotionEvent.ACTION_DOWN) {
                    println("손가락 눌렸음: " + curX + ", " + curY);
                } else if (action == MotionEvent.ACTION_MOVE) {
                    println("손가락 움직임: " + curX + ", " + curY);
                } else if (action == MotionEvent.ACTION_UP) {
                    println("손가락 떼졌음: " + curX + ", " + curY);
                }
                return true;
            }
        });
'''

### ▶️ 토스트와 대화상자

1) 토스트 보여주기

- 토스트 메시지 : 간단한 메시지를 잠깐 보여주었다가 없어지는 뷰, 앱 화면에 종속되지 않음
->  실행영역보다 앞 쪽에 보이는 뷰이기 때문에 앱이 화면에 보이지 않는 상태에서도 토스트가 보일 수 있음
- 위치/ 색상/ 모양 변경 가능
- 토스트 메시지와 비슷하게 스낵바 사용 (스낵바는 외부 라이브러리 이용 & 스낵바는 안 꺼지게 할 수 있어 토스트 메시지보다 유용하게 사용 가능)

'''java
Button button2 = (Button) findViewById(R.id.button2);
        button2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                LayoutInflater inflater = getLayoutInflater();
                View layout = inflater.inflate(R.layout.toastborder, (ViewGroup) findViewById(R.id.toast_layout_root));
                TextView text = (TextView) layout.findViewById(R.id.text);
                text.setText("모양을 바꾼 토스트");

                Toast toast = new Toast(getApplicationContext());
                toast.setGravity(Gravity.CENTER, 0, -100);
                toast.setDuration(Toast.LENGTH_LONG);
                toast.setView(layout);

                toast.show();
            }
        });
    Button button3 = (Button) findViewById(R.id.button3);
    button3.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            Snackbar.make(view, "스낵바 입니다.", Snackbar.LENGTH_LONG).show();
        }
    });
'''

2) 알림 대화상자 보여주기

- 알림 대화상자 : 사용자가 예/아니오 // 확인/취소 가능

'''java
public void showMessage() {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("안내");
        builder.setMessage("종료하시겠습니까?");
        builder.setIcon(android.R.drawable.ic_dialog_alert);

        builder.setPositiveButton("예", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                Snackbar.make(textView, "예 버튼이 눌렸습니다.", Snackbar.LENGTH_LONG).show();
            }
        });

        builder.setNegativeButton("아니오", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                Snackbar.make(textView, "아니오 버튼이 눌렸습니다.", Snackbar.LENGTH_LONG).show();
            }
        });
        AlertDialog dialog = builder.create();
        dialog.show();
    }
'''

### ▶️ 비트맵 버튼 만들기

1) 나인패치 이미지

- 버튼이나 텍스트뷰의 배경으로 이미지를 설정하면 그 이미지는 자동으로 버튼이나 텍스트 뷰의 크기에 맞춰짐 -> 이미지의 크기가 늘어날 때 일부분이 깨져 보이는 문제가 생기기도 함
- 나인패치 이미지 : 원래 이미지보다 한 픽셀씩 크게 만들고 가장자리 픽셀에는 늘어날 수 있는지, 늘어나면 안되는지를 색상으로 구분하여 넣어줌

2) 비트맵 버튼 만들기
- 버튼을 상속 -> 새로운 버튼을 만들면 원하는 기능 추가 가능 (ex touch와 같은 event 처리 -> normal/ onClicked 다르게 설정 가능)
- 뷰를 상속해서 새로운 뷰를 만든 경우 (비트맵 버튼과 같은 경우) XML 레이아웃에 추가할 때 패키지 명까지 같이 넣어줘야 함

'''xml
 <org.techtown.button.BitmapButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!" />
'''

### ▶️ 인플레이션 이해하기

- 안드로이드 : XML 레이아웃 파일 & java 소스파일이 한 세트로 화면 구성
- 분리해둔 XML 레이아웃 파일에 들어있는 버튼을 소스 파일에서도 인식할 때 인플레이션 과정 필요
- 전체 화면 MainActivity에서 인식할 때 setContentView 메소드의 parameter로 해당 XML 레이아웃 파일 지정 -> 내부적으로 인플레이션 과정 진행
- XML 레이아웃 파일 안에 들어있는 뷰 태그들을 이용해 뷰 객체를 메모리에 만드는 것이 인플레이션 과정
- XML 레이아웃 파일의 내용이 메모리에 객체로 만들어지면 소스 코드에서는 그 객체들을 찾아 사용할 수 있음 (findViewById 메소드 이용)
- 부분 화면의 경우 setContentView 사용 불가 layout inflator service로 직접 인플레이션 해줘야 함 

'''java
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        container = (FrameLayout) findViewById(R.id.container);

        Button button = (Button)findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                LayoutInflater inflater = (LayoutInflater) getSystemService(Context.LAYOUT_INFLATER_SERVICE);
                inflater.inflate(R.layout.sub1, container, true);

            }
        });
    }
'''

### ▶️ 리스트뷰 만들기
 
 1) 리스트뷰 만들기

 - 리스트 안에 들어가 있는 각각의 데이터는 같은 모양이 반복되면서 보임 (레이아웃이 동일) -> 레이아웃 먼저 별도로 정의
 - 여러 개의 아이템 중에서 하나를 선택하는 방식을 가진 선택 위젯 (리스트뷰, 스피너 등)은 어댑터를 사용
 - 각각의 아이템은 독립적인 뷰로 만들어지고 이 뷰들이 모여있는 형태를 유지해 주는 것이 리스트뷰
 - 어댑터를 리스트뷰에 설정하면 리스트뷰는 어댑터에게 데이터나 각각의 아이템을 위한 뷰를 물어봄 -> 리스트뷰는 어댑터가 만들어준 뷰를 getView 메소드를 이용해 반환 받은 뒤 보여줌
 
 '''java
 class SingerAdapter extends BaseAdapter{
        ArrayList<SingerItem> items = new ArrayList<SingerItem>();

        @Override
        public int getCount() {
            return items.size();
        }

        public void addItem(SingerItem item){
            items.add(item);

        }

        @Override
        public Object getItem(int i) {
            return items.get(i);
        }

        @Override
        public long getItemId(int i) {
            return i;
        }

        @Override
        public View getView(int i, View view, ViewGroup viewGroup) {
            SingerItemView v = null;
            if(view == null){
                v = new SingerItemView(getApplicationContext());
            } else{
                v = (SingerItemView) view;
            }
            SingerItem item = items.get(i);
            v.setName(item.getName());
            v.setMobile(item.getMobile());
            v.setImage(item.getResId());

            return v;
        }
    }
'''

 2) 스피너 사용하기
 
 - 스피너 (=콤보박스) 역시 선택 위젯이기 때문에 어댑터 사용
 - 스피너의 경우 한 항목당 textView 하나만 보여주는 경우가 많아 ArrayAdapter을 사용하는 것이 유리
 - 스피너는 이미 선택된 아이템이 보이는 뷰와 아이템을 선택하기 위해 보이는 뷰가 서로 다름 -> 두 개의 뷰가 필요

'''java
Spinner spinner = (Spinner) findViewById(R.id.spinner);
        ArrayAdapter<String> adapter = new ArrayAdapter<String>(
                this, android.R.layout.simple_spinner_item, items
        );
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
        spinner.setAdapter(adapter);

        spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                textView.setText(items[i]);
            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {
                textView.setText("선택: ");

            }
        });
'''

 3) 그리드뷰 사용하기
 
 - 그리드뷰는 격자 형태로 아이템들이 보이는 위젯 -> column 지정 가능
 (리스트뷰를 격자모양으로 바꾼 것과 동일)
 - 리스트뷰와 매우 유사, 코드도 거의 동일하게 사용

## 👊 Git (공부한 소스코드 공유)

| 작성자 |           주소            |
| :----: | :-----------------------: |
| 이수은 | 'https://github.com/CLUG-kr/AndOne.git' |
