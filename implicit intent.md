# implicit-intent
//handling other activity's from my  activity using intent  

package com.example.implecit_intent;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {
    Button launchmap,launchmarket,sendemail;
    EditText Enter_email;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // i have linked the all the xml file with my boiler plate code which is called the java code
        setContentView(R.layout.activity_main);
        Enter_email=findViewById(R.id.Enter_email);
        launchmap=findViewById(R.id.launchmap);
        launchmarket=findViewById(R.id.launchmarket);
        sendemail=findViewById(R.id.sendemail);
        // here the linking process ends
        //
        //code to open map and search or the location which has been given in the fom of string
        launchmap.setOnClickListener(new View.OnClickListener() {
            Intent intent=null,choose=null;
            @Override
            public void onClick(View v) {
                intent=new Intent(Intent.ACTION_VIEW);
                choose=Intent.createChooser(intent,"launch now");
                intent.setData(Uri.parse("geo:19.076,72.8777"));
                startActivity(choose);
            }
        });
        //code to open map ends here
        //
        //code to open any url of the website
        launchmarket.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
               Intent intent=new Intent(Intent.ACTION_VIEW );
               intent.setData(Uri.parse("https://www.pcvibe.net/"));
               Intent chooser=new Intent();
               chooser=Intent.createChooser(intent,"launch market");
               startActivity(chooser);
            }
        });
        //code to open any url is being ended here
        //
        //code to send email
        //data which has been sended is the email id to who we have to send the email and the subject to whom we have to send the email one more thing left is the text which is the body of the email
        sendemail.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String subject,text ,to;
                subject=Enter_email.getText().toString();
                text=Enter_email.getText().toString();
                to=Enter_email.getText().toString();
                Intent intent=new Intent(Intent.ACTION_SEND);
                intent.putExtra(Intent.EXTRA_EMAIL,new String[]{to});
                intent.putExtra(Intent.EXTRA_SUBJECT,subject);
                intent.putExtra(Intent.EXTRA_TEXT,text);
                intent.setType("message/rfc822");
                Intent chooser=new Intent();
                chooser=Intent.createChooser(intent,"select an app");
                startActivity(chooser);
            }
        });
        // code to send email ends here
    }
}
