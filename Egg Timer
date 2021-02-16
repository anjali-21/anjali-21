package com.anjali.eggtimer;

import androidx.appcompat.app.AppCompatActivity;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.os.CountDownTimer;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.SeekBar;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    TextView countdownTextView ;
    Button gobutton;
    SeekBar eggSeekBar;
    CountDownTimer CountDownTimer;
    Boolean isActive = false;
    MediaPlayer mp;
    public void resetTimer(){
        countdownTextView.setText("00:30");
        eggSeekBar.setProgress(30);
        eggSeekBar.setEnabled(true);
        CountDownTimer.cancel();
        gobutton.setText("GO!");
        isActive=false;
    }
    public void buttonclicked(View view) {
        if (isActive){
           resetTimer();
        }
        else{
            gobutton.setText("STOP!");
            eggSeekBar.setEnabled(false);
            isActive=true;
        CountDownTimer=new CountDownTimer(eggSeekBar.getProgress()*1000+100,1000){
            @Override
            public void onTick(long millisUntilFinished) {
                updateTimer((int)millisUntilFinished/1000);

            }


            @Override
            public void onFinish() {
                mp = MediaPlayer.create(getApplicationContext(),R.raw.aud2);
                mp.start();
                resetTimer();
            }
        }.start();
    }}
    public void updateTimer(int progress){
        int minutes = progress/60;
        int seconds = progress - minutes *60;
        String secs=Integer.toString(seconds);
        String mins=Integer.toString(minutes);
        if (secs.equals("0")){
            secs="00";
        }
        if (Integer.parseInt(secs)<10 && Integer.parseInt(secs)>0)
            secs="0"+secs;
        if (Integer.parseInt(mins)==60 || Integer.parseInt(mins)==0)
            mins="00";
        countdownTextView.setText(mins+":"+secs);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        eggSeekBar = findViewById(R.id.eggSeekBar);
        countdownTextView = findViewById(R.id.countdownTextView);
        gobutton=findViewById(R.id.gobutton);
        eggSeekBar.setMax(600);
        eggSeekBar.setProgress(30);
        eggSeekBar.setOnSeekBarChangeListener(
                new SeekBar.OnSeekBarChangeListener() {
                    @Override
                    public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                        updateTimer(progress);
                    }

                    @Override
                    public void onStartTrackingTouch(SeekBar seekBar) {

                    }

                    @Override
                    public void onStopTrackingTouch(SeekBar seekBar) {

                    }
                }
        );
    }
}
