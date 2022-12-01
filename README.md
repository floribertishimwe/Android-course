Login interface
===============
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        setTitle("BMI App");
        Button login= (Button)  findViewById(R.id.check_password_username);
        username=(EditText) findViewById(R.id.check_username);
        password=(EditText) findViewById(R.id.check_password);
        login.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if( username.getText().toString().equals("") || password.getText().toString().equals("")){
                        Toast.makeText(MainActivity.this, "Please fill out the  Fields.", Toast.LENGTH_SHORT).show();
                }
                try {
                    InputStream in = getAssets().open("file.txt");
                  BufferedReader br = new BufferedReader(new InputStreamReader(in));
                    String text="";
                    int counter=0;
                    while ((text = br.readLine()) != null) {

                        String[] credentials = text.split(" ");
                        if (username.getText().toString().equals(credentials[0]) && password.getText().toString().equals(credentials[1])) {
                            counter =1;
                        Intent intent = new Intent(getApplicationContext(), MainActivity2.class);//                            intent.putExtra("username", username.getText().toString());
                        startActivity(intent);

                        }

                    }
                    if (counter==0){
                        Toast.makeText(getBaseContext(), "Invalid username or password " , Toast.LENGTH_LONG).show();
                    }


                }catch (IOException ex){
                    ex.printStackTrace();
                }

            }
        });

    }
}


Calculating  BMI
==================
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        setTitle("BMI App");
        Button login= (Button)  findViewById(R.id.check_password_username);
        username=(EditText) findViewById(R.id.check_username);
        password=(EditText) findViewById(R.id.check_password);
        login.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if( username.getText().toString().equals("") || password.getText().toString().equals("")){
                        Toast.makeText(MainActivity.this, "Please fill out the  Fields.", Toast.LENGTH_SHORT).show();
                }
                try {
                    InputStream in = getAssets().open("file.txt");
                  BufferedReader br = new BufferedReader(new InputStreamReader(in));
                    String text="";
                    int counter=0;
                    while ((text = br.readLine()) != null) {

                        String[] credentials = text.split(" ");
                        if (username.getText().toString().equals(credentials[0]) && password.getText().toString().equals(credentials[1])) {
                            counter =1;
                        Intent intent = new Intent(getApplicationContext(), MainActivity2.class);//                            intent.putExtra("username", username.getText().toString());
                        startActivity(intent);

                        }

                    }
                    if (counter==0){
                        Toast.makeText(getBaseContext(), "Invalid username or password " , Toast.LENGTH_LONG).show();
                    }


                }catch (IOException ex){
                    ex.printStackTrace();
                }

            }
        });

    }
}


Connecting to another app
==========================
  protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_3);
        setTitle("BMICalculator");
        Intent intent= getIntent();
    }
}




Recieving from activity
=========================
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        IntentFilter  intentFilter = new IntentFilter("BMICondition");
        MyReceiver ObjReceiver= new MyReceiver () ;
        registerReceiver(ObjReceiver,intentFilter);
    }
}



Providing the toasts
======================
public void onReceive(Context context, Intent intent) {
        // TODO: This method is called when the BroadcastReceiver is receiving
        // an Intent broadcast.
        String condition= intent.getExtras().getString("condition");
        if(condition.equals("Underweight")){
            Toast.makeText(context, "Improve your Nutrition ", Toast.LENGTH_SHORT).show();

        }
        else if( condition.equals("Normal")){
            Toast.makeText(context, "You are Healthy ", Toast.LENGTH_SHORT).show();

        }
        else if( condition.equals("Overweight")){
            Toast.makeText(context, "Reduce Fats \n Exercise More  ", Toast.LENGTH_SHORT).show();

        }
        else{
            Toast.makeText(context, "Consult the Doctor \n You need doctor's advice ", Toast.LENGTH_SHORT).show();
        }

    }
}

MAnifest Files(Reciever app)
============================
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.RecieverApp"
        tools:targetApi="31">
        <receiver
            android:name=".MyReceiver"
            android:enabled="true"
            android:exported="true">
        <intent-filter>

            <action android:name="BMICondition"></action>
        </intent-filter>


        </receiver>

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>


MAnifest Files(Sending Appp)
============================

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApplication"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity2"
            android:exported="false">
            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>




