# ๐ข (2์ฃผ์ฐจ) ์คํฐ๋ ์ผ์ง

> ## ์์ฑ์ : ์ด์์ 
>
> ## ์์ฑ ๋ ์ง : 2021.10.01
>
> ## ์ฐธ์ฌ์ : ๊ณฝํฌ์ค ์ ์ง์ ์ด์์ ํ์ข์ฑ

## โ ์ด๋ฒ์ฃผ ๊ณต๋ถ ๋ด์ฉ : ์ด๋ฒคํธ์ ๋ฆฌ์คํธ๋ทฐ

### โถ๏ธ ์คํฌ๋กค๋ทฐ ์ฌ์ฉํ๊ธฐ

1) ํ์ด๋ธ ๋ ์ด์์

- ๊ฒฉ์ ๋ชจ์์ผ๋ก ๋ทฐ๋ฅผ ๋ฐฐ์นํ  ๋ ์ฌ์ฉ
- ํ ์ถ๊ฐ ๊ฐ๋ฅ
- ๊ฐ๊ฐ์ <TableRow> ์์๋ ์ฌ๋ฌ ๊ฐ์ ๋ทฐ๊ฐ ๋ค์ด๊ฐ ์ ์๋ ๊ตฌ์กฐ๋ก ๋์ด ์์

2) ์คํฌ๋กค๋ทฐ

- ๊ธ์๋ ์ด๋ฏธ์ง๊ฐ ๋ค์ด๊ฐ ๋ทฐ๊ฐ ํ๋ฉด ์์ญ์ ๋ฒ์ด๋๋ฉด ๋ณด์ด์ง ์๊ฒ ๋จ
- ์คํฌ๋กค๋ทฐ๋ก ์ด๋ฏธ์ง๋ทฐ/ํ์คํธ๋ทฐ ๋ฑ์ ๊ฐ์ธ์ฃผ๊ธฐ๋ง ํ๋ฉด ์คํฌ๋กค๋ทฐ๊ฐ ๋ทฐ์ ์์ญ์ ๊ณ์ฐํ์ฌ ์๋์ผ๋ก ์คํฌ๋กค ์์ฑ

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
                android:text="์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n์๋ํ์ธ์.\n" />
        </LinearLayout>
    </ScrollView>
'''

### โถ๏ธ ์ด๋ฒคํธ ์ดํดํ๊ธฐ

1) ์ด๋ฒคํธ ์ฒ๋ฆฌ ์ดํดํ๊ธฐ

- ์ด๋ฒคํธ์ ์ข๋ฅ๋ ๋ค์ (ํฐ์น ์ด๋ฒคํธ, ํด๋ฆญ ์ด๋ฒคํธ, ํค ์ด๋ฒคํธ ๋ฑ)
- ์ด๋ฒคํธ๋ ๋ฆฌ์ค๋๋ฅผ ์ด์ฉํ์ฌ ๋ค๋ฃฐ ์ ์์
- click -> touch event๋ก ์ธ๋ถํ ๊ฐ๋ฅ
- gesture event : touch event์ ์ผ์  ํจํด์ ๋์  ๊ณ์ฐํด ์ค (ex ์๋)
- event ๋ฐ์์ ํ ์คํธ ๋ฉ์์ง, ์๋ฆผ ๋ํ์์, ๊ฐ๋จํ ์ ๋๋ฉ์ด์ ๋ฑ์ ๋ณด์ฌ์ฃผ๊ฒ ๋ง๋ค ์ ์์

'''java
View view = findViewById(R.id.view);
        view.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                int action = motionEvent.getAction();
                float curX = motionEvent.getX();
                float curY = motionEvent.getY();

                if (action == MotionEvent.ACTION_DOWN) {
                    println("์๊ฐ๋ฝ ๋๋ ธ์: " + curX + ", " + curY);
                } else if (action == MotionEvent.ACTION_MOVE) {
                    println("์๊ฐ๋ฝ ์์ง์: " + curX + ", " + curY);
                } else if (action == MotionEvent.ACTION_UP) {
                    println("์๊ฐ๋ฝ ๋ผ์ก์: " + curX + ", " + curY);
                }
                return true;
            }
        });
'''

### โถ๏ธ ํ ์คํธ์ ๋ํ์์

1) ํ ์คํธ ๋ณด์ฌ์ฃผ๊ธฐ

- ํ ์คํธ ๋ฉ์์ง : ๊ฐ๋จํ ๋ฉ์์ง๋ฅผ ์ ๊น ๋ณด์ฌ์ฃผ์๋ค๊ฐ ์์ด์ง๋ ๋ทฐ, ์ฑ ํ๋ฉด์ ์ข์๋์ง ์์
->  ์คํ์์ญ๋ณด๋ค ์ ์ชฝ์ ๋ณด์ด๋ ๋ทฐ์ด๊ธฐ ๋๋ฌธ์ ์ฑ์ด ํ๋ฉด์ ๋ณด์ด์ง ์๋ ์ํ์์๋ ํ ์คํธ๊ฐ ๋ณด์ผ ์ ์์
- ์์น/ ์์/ ๋ชจ์ ๋ณ๊ฒฝ ๊ฐ๋ฅ
- ํ ์คํธ ๋ฉ์์ง์ ๋น์ทํ๊ฒ ์ค๋ต๋ฐ ์ฌ์ฉ (์ค๋ต๋ฐ๋ ์ธ๋ถ ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ด์ฉ & ์ค๋ต๋ฐ๋ ์ ๊บผ์ง๊ฒ ํ  ์ ์์ด ํ ์คํธ ๋ฉ์์ง๋ณด๋ค ์ ์ฉํ๊ฒ ์ฌ์ฉ ๊ฐ๋ฅ)

'''java
Button button2 = (Button) findViewById(R.id.button2);
        button2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                LayoutInflater inflater = getLayoutInflater();
                View layout = inflater.inflate(R.layout.toastborder, (ViewGroup) findViewById(R.id.toast_layout_root));
                TextView text = (TextView) layout.findViewById(R.id.text);
                text.setText("๋ชจ์์ ๋ฐ๊พผ ํ ์คํธ");

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
            Snackbar.make(view, "์ค๋ต๋ฐ ์๋๋ค.", Snackbar.LENGTH_LONG).show();
        }
    });
'''

2) ์๋ฆผ ๋ํ์์ ๋ณด์ฌ์ฃผ๊ธฐ

- ์๋ฆผ ๋ํ์์ : ์ฌ์ฉ์๊ฐ ์/์๋์ค // ํ์ธ/์ทจ์ ๊ฐ๋ฅ

'''java
public void showMessage() {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("์๋ด");
        builder.setMessage("์ข๋ฃํ์๊ฒ ์ต๋๊น?");
        builder.setIcon(android.R.drawable.ic_dialog_alert);

        builder.setPositiveButton("์", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                Snackbar.make(textView, "์ ๋ฒํผ์ด ๋๋ ธ์ต๋๋ค.", Snackbar.LENGTH_LONG).show();
            }
        });

        builder.setNegativeButton("์๋์ค", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                Snackbar.make(textView, "์๋์ค ๋ฒํผ์ด ๋๋ ธ์ต๋๋ค.", Snackbar.LENGTH_LONG).show();
            }
        });
        AlertDialog dialog = builder.create();
        dialog.show();
    }
'''

### โถ๏ธ ๋นํธ๋งต ๋ฒํผ ๋ง๋ค๊ธฐ

1) ๋์ธํจ์น ์ด๋ฏธ์ง

- ๋ฒํผ์ด๋ ํ์คํธ๋ทฐ์ ๋ฐฐ๊ฒฝ์ผ๋ก ์ด๋ฏธ์ง๋ฅผ ์ค์ ํ๋ฉด ๊ทธ ์ด๋ฏธ์ง๋ ์๋์ผ๋ก ๋ฒํผ์ด๋ ํ์คํธ ๋ทฐ์ ํฌ๊ธฐ์ ๋ง์ถฐ์ง -> ์ด๋ฏธ์ง์ ํฌ๊ธฐ๊ฐ ๋์ด๋  ๋ ์ผ๋ถ๋ถ์ด ๊นจ์ ธ ๋ณด์ด๋ ๋ฌธ์ ๊ฐ ์๊ธฐ๊ธฐ๋ ํจ
- ๋์ธํจ์น ์ด๋ฏธ์ง : ์๋ ์ด๋ฏธ์ง๋ณด๋ค ํ ํฝ์์ฉ ํฌ๊ฒ ๋ง๋ค๊ณ  ๊ฐ์ฅ์๋ฆฌ ํฝ์์๋ ๋์ด๋  ์ ์๋์ง, ๋์ด๋๋ฉด ์๋๋์ง๋ฅผ ์์์ผ๋ก ๊ตฌ๋ถํ์ฌ ๋ฃ์ด์ค

2) ๋นํธ๋งต ๋ฒํผ ๋ง๋ค๊ธฐ
- ๋ฒํผ์ ์์ -> ์๋ก์ด ๋ฒํผ์ ๋ง๋ค๋ฉด ์ํ๋ ๊ธฐ๋ฅ ์ถ๊ฐ ๊ฐ๋ฅ (ex touch์ ๊ฐ์ event ์ฒ๋ฆฌ -> normal/ onClicked ๋ค๋ฅด๊ฒ ์ค์  ๊ฐ๋ฅ)
- ๋ทฐ๋ฅผ ์์ํด์ ์๋ก์ด ๋ทฐ๋ฅผ ๋ง๋  ๊ฒฝ์ฐ (๋นํธ๋งต ๋ฒํผ๊ณผ ๊ฐ์ ๊ฒฝ์ฐ) XML ๋ ์ด์์์ ์ถ๊ฐํ  ๋ ํจํค์ง ๋ช๊น์ง ๊ฐ์ด ๋ฃ์ด์ค์ผ ํจ

'''xml
 <org.techtown.button.BitmapButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!" />
'''

### โถ๏ธ ์ธํ๋ ์ด์ ์ดํดํ๊ธฐ

- ์๋๋ก์ด๋ : XML ๋ ์ด์์ ํ์ผ & java ์์คํ์ผ์ด ํ ์ธํธ๋ก ํ๋ฉด ๊ตฌ์ฑ
- ๋ถ๋ฆฌํด๋ XML ๋ ์ด์์ ํ์ผ์ ๋ค์ด์๋ ๋ฒํผ์ ์์ค ํ์ผ์์๋ ์ธ์ํ  ๋ ์ธํ๋ ์ด์ ๊ณผ์  ํ์
- ์ ์ฒด ํ๋ฉด MainActivity์์ ์ธ์ํ  ๋ setContentView ๋ฉ์๋์ parameter๋ก ํด๋น XML ๋ ์ด์์ ํ์ผ ์ง์  -> ๋ด๋ถ์ ์ผ๋ก ์ธํ๋ ์ด์ ๊ณผ์  ์งํ
- XML ๋ ์ด์์ ํ์ผ ์์ ๋ค์ด์๋ ๋ทฐ ํ๊ทธ๋ค์ ์ด์ฉํด ๋ทฐ ๊ฐ์ฒด๋ฅผ ๋ฉ๋ชจ๋ฆฌ์ ๋ง๋๋ ๊ฒ์ด ์ธํ๋ ์ด์ ๊ณผ์ 
- XML ๋ ์ด์์ ํ์ผ์ ๋ด์ฉ์ด ๋ฉ๋ชจ๋ฆฌ์ ๊ฐ์ฒด๋ก ๋ง๋ค์ด์ง๋ฉด ์์ค ์ฝ๋์์๋ ๊ทธ ๊ฐ์ฒด๋ค์ ์ฐพ์ ์ฌ์ฉํ  ์ ์์ (findViewById ๋ฉ์๋ ์ด์ฉ)
- ๋ถ๋ถ ํ๋ฉด์ ๊ฒฝ์ฐ setContentView ์ฌ์ฉ ๋ถ๊ฐ layout inflator service๋ก ์ง์  ์ธํ๋ ์ด์ ํด์ค์ผ ํจ 

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

### โถ๏ธ ๋ฆฌ์คํธ๋ทฐ ๋ง๋ค๊ธฐ
 
 1) ๋ฆฌ์คํธ๋ทฐ ๋ง๋ค๊ธฐ

 - ๋ฆฌ์คํธ ์์ ๋ค์ด๊ฐ ์๋ ๊ฐ๊ฐ์ ๋ฐ์ดํฐ๋ ๊ฐ์ ๋ชจ์์ด ๋ฐ๋ณต๋๋ฉด์ ๋ณด์ (๋ ์ด์์์ด ๋์ผ) -> ๋ ์ด์์ ๋จผ์  ๋ณ๋๋ก ์ ์
 - ์ฌ๋ฌ ๊ฐ์ ์์ดํ ์ค์์ ํ๋๋ฅผ ์ ํํ๋ ๋ฐฉ์์ ๊ฐ์ง ์ ํ ์์ ฏ (๋ฆฌ์คํธ๋ทฐ, ์คํผ๋ ๋ฑ)์ ์ด๋ํฐ๋ฅผ ์ฌ์ฉ
 - ๊ฐ๊ฐ์ ์์ดํ์ ๋๋ฆฝ์ ์ธ ๋ทฐ๋ก ๋ง๋ค์ด์ง๊ณ  ์ด ๋ทฐ๋ค์ด ๋ชจ์ฌ์๋ ํํ๋ฅผ ์ ์งํด ์ฃผ๋ ๊ฒ์ด ๋ฆฌ์คํธ๋ทฐ
 - ์ด๋ํฐ๋ฅผ ๋ฆฌ์คํธ๋ทฐ์ ์ค์ ํ๋ฉด ๋ฆฌ์คํธ๋ทฐ๋ ์ด๋ํฐ์๊ฒ ๋ฐ์ดํฐ๋ ๊ฐ๊ฐ์ ์์ดํ์ ์ํ ๋ทฐ๋ฅผ ๋ฌผ์ด๋ด -> ๋ฆฌ์คํธ๋ทฐ๋ ์ด๋ํฐ๊ฐ ๋ง๋ค์ด์ค ๋ทฐ๋ฅผ getView ๋ฉ์๋๋ฅผ ์ด์ฉํด ๋ฐํ ๋ฐ์ ๋ค ๋ณด์ฌ์ค
 
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

 2) ์คํผ๋ ์ฌ์ฉํ๊ธฐ
 
 - ์คํผ๋ (=์ฝค๋ณด๋ฐ์ค) ์ญ์ ์ ํ ์์ ฏ์ด๊ธฐ ๋๋ฌธ์ ์ด๋ํฐ ์ฌ์ฉ
 - ์คํผ๋์ ๊ฒฝ์ฐ ํ ํญ๋ชฉ๋น textView ํ๋๋ง ๋ณด์ฌ์ฃผ๋ ๊ฒฝ์ฐ๊ฐ ๋ง์ ArrayAdapter์ ์ฌ์ฉํ๋ ๊ฒ์ด ์ ๋ฆฌ
 - ์คํผ๋๋ ์ด๋ฏธ ์ ํ๋ ์์ดํ์ด ๋ณด์ด๋ ๋ทฐ์ ์์ดํ์ ์ ํํ๊ธฐ ์ํด ๋ณด์ด๋ ๋ทฐ๊ฐ ์๋ก ๋ค๋ฆ -> ๋ ๊ฐ์ ๋ทฐ๊ฐ ํ์

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
                textView.setText("์ ํ: ");

            }
        });
'''

 3) ๊ทธ๋ฆฌ๋๋ทฐ ์ฌ์ฉํ๊ธฐ
 
 - ๊ทธ๋ฆฌ๋๋ทฐ๋ ๊ฒฉ์ ํํ๋ก ์์ดํ๋ค์ด ๋ณด์ด๋ ์์ ฏ -> column ์ง์  ๊ฐ๋ฅ
 (๋ฆฌ์คํธ๋ทฐ๋ฅผ ๊ฒฉ์๋ชจ์์ผ๋ก ๋ฐ๊พผ ๊ฒ๊ณผ ๋์ผ)
 - ๋ฆฌ์คํธ๋ทฐ์ ๋งค์ฐ ์ ์ฌ, ์ฝ๋๋ ๊ฑฐ์ ๋์ผํ๊ฒ ์ฌ์ฉ

## ๐ Git (๊ณต๋ถํ ์์ค์ฝ๋ ๊ณต์ )

| ์์ฑ์ |           ์ฃผ์            |
| :----: | :-----------------------: |
| ์ด์์ | 'https://github.com/CLUG-kr/AndOne.git' |
