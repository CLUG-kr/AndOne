# π’ (1μ£Όμ°¨) μ€ν°λ μΌμ§

> ## μμ±μ : μ μ§μ
>
> ## μμ± λ μ§ : 2021.09.25
>
> ## μ°Έμ¬μ : κ³½ν¬μ€ μ μ§μ μ΄μμ νμ’μ±

## β μ΄λ²μ£Ό κ³΅λΆ λ΄μ© : λ μ΄μμ λ§λ€κΈ°

### βΆοΈ μ μ½ λ μ΄μμ

- νλ‘μ νΈλ₯Ό μμ±νλ©΄ μλμΌλ‘ λ§λ€μ΄μ§λ€
- μ μ½μ‘°κ±΄μ μ΄μ©ν΄ κ·Έ μμ μΆκ°λ λ·°λ€μΉλ₯Ό κ²°μ 
- μ μ½μ‘°κ±΄μ μ°κ²°μ μΌλ‘ λ§λ€ μ μλ€
- μ°κ²°μ μ λ·°μ μ°κ²°μ μ λ€λ₯Έ λ·°λ λ μ΄μμκ³Ό μ°κ²°νμ¬ λ§λ€ μ μλ€
- μ°κ²°μ μ λ·°κ° μ΄λμ μμΉν  μ§ μ μ μλλ‘ μ°κ²°νλ κ²μ΄ μ€μνλ€
  
### βΆοΈ λ¦¬λμ΄ λ μ΄μμ

- oirentation: λ¦¬λμ΄ λ μ΄μμμμ λ°©ν₯μ κ²°μ νλ μμ±.
- layout_gravity: λ¦¬λμ΄ λ μ΄μμ μμ μλ λ·°λ₯Ό μ λ ¬νλ μμ±.
- gravity: λ·° μμ μλ λ΄μ©λ¬Όμ μ λ ¬νλ μμ±.
- layout_margin: λ μ΄μμμ νλλ¦¬λ‘ λΆν° λ·°μ νλλ¦¬λ₯Ό μΌλ§νΌ λμΈ μ§ μ νλ μμ±. μνμ’μ° λͺ¨λ κ°λ₯.
- padding: λ·°μ λ΄μ©λ¬Όμ λ·°μ νλλ¦¬μ μΌλ§λ λμΈμ§ μ νλ μμ±.
- layout_weight: μ¬μ  κ³΅κ°μμ λ·°μ κ³΅κ°μ λΆν νλ μμ±. λΉλ‘μμ΄λ μ μ¬.
  
'''xml
<Button
        android:id="@+id/button4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_weight="3"
        android:text="Button" />
'''
  
### βΆοΈ μλ λ μ΄μμ

- λΆλͺ¨ λ μ΄μμμ΄λ λ€λ₯Έ λ·°λ€μ μλμ  μμΉλ₯Ό μ΄μ©ν΄ λ°°μΉνλ λ μ΄μ΄.
- μ μ½ λ μ΄μ΄μ μ μ¬.
- μ€μ΅νλ λ΄μ© μ€, κ°μ΄λ° μλ λ²νΌμ μ½λ
  
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
  
### βΆοΈ νλ μ λ μ΄μμ

- ν λ²μ νλμ λ·°λ§ λ³΄μ¬μ£Όλ λ μ΄μμ
- μ£Όλ‘ μ¬λ¬κ°μ λ·°λ₯Ό μ€μ²©μν¬ λ μ¬μ©ν¨
- visibility: λ·°λ₯Ό λ³΄μ¬μ£Όλ μμ±. λ³΄μ΄κ³  μΆμ λ visible, λ³΄μ¬μ£Όκ³  μΆμ§ μμ λ invisibleμ΄λ goneμ μ¬μ©
- μ΄λ° μμ±μ μ΄μ©ν΄ νΉμ  μ‘°κ±΄μ λ°λΌ λ³Ό μ μλ λ·°λ₯Ό λ°κΏ μ μμ. (e.g. λ²νΌμ λλ₯΄λ©΄ μ΄λ―Έμ§κ° λ°λ)
- mainactivity.java μ½λ. ν΄λ¦­νμ λ μ΄λ―Έμ§ λ³ννλ μ½λ.
  
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
  
### βΆοΈ λλ‘μ΄λΈ λ§λ€κΈ°

- μ½λλ xml νμΌλ‘ κ·Έλν½μ λ§λ€ μ μλλ° κ·Έκ²μ λλ‘μ΄λΈμ΄λΌκ³  ν¨
- λλ‘μ΄λΈμ μ’λ₯: λΉνΈλ§΅ λλ‘μ΄λΈ, μν λλ‘μ΄λΈ, μ ν λλ‘μ΄λΈ, μμ΄ν λλ‘μ΄λΈ
- λΉνΈλ§΅ λλ‘μ΄λΈ: μ΄λ―Έμ§ νμΌμ λ³΄μ¬μ€ λ μ¬μ©. λΉνΈλ§΅ μ΄λ―Έμ§λ₯Ό λλ‘μ΄λΈλ‘ λ³κ²½ κ°λ₯. κ·Έ λ°λλ κ°λ₯
- μ ν λλ‘μ΄λΈ: λ κ°μ λλ‘μ΄λΈ κ°μ λ°λλλ‘ λ§λ€ μ μμ
- μν λλ‘μ΄λΈ: λ·°μ μνμ λ°λΌ λ·°μ λ³΄μ¬μ€ κ·Έλν½μ λ€λ₯΄κ² μ§μ ν  μ μμ. state_press(λλ¦° μν), state_focused(ν¬μ»€μ€λ₯Ό λ°μ μν) λ± state_λ‘ μμνλ μμ±μ μ΄μ©ν΄ λ§λ€ μ μλ€.
-μμ΄ν λλ‘μ΄λΈ: XMLλ‘ λνμ κ·Έλ¦΄ μ μμ. μ΅μμ νκ·Έλ₯Ό shapeλ‘ μ§μ νλ©΄ λν νλλ₯Ό μ§μ ν  μ μλ€. stroke(νλλ¦¬ μμ±), width(λκ» μμ±), color(μμ μμ±), solid(λν μμ μ±μ°λ μμ μμ±), gradient(κ·ΈλΌλ°μ΄μμ μ€ μ μλ νκ·Έ)
- layer_list: μ¬λ¬κ°μ item νκ·Έκ° λ€μ΄κ° μ μλ νκ·Έ. μ΄λ₯Ό μ΄μ©νμ¬ μ¬λ¬ κ·Έλν½μ νλμ xmlμ λ£μ μ μλ€.  
- μμ΄ν λλ‘μ΄λΈ μ€ κ·ΈλΌλ°μ΄μ λ£λ μ€μ΅ μ½λ

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

## π Git (κ³΅λΆν μμ€μ½λ κ³΅μ )

| μμ±μ |           μ£Όμ            |
| :----: | :-----------------------: |
| μ μ§μ | 'https://github.com/CLUG-kr/AndOne.git' |
