package umn.ac.id;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

import androidx.annotation.Nullable;

public class DBHelper extends SQLiteOpenHelper {
    public static final  String DBNAME = "Login.db";

    public DBHelper(Context context) {
        super(context,"Login.db" , null, 1);
    }

    @Override
    public void onCreate(SQLiteDatabase MYDB) {
        MYDB.execSQL("create Table users(username TEXT primary key, firstname TEXT, lastname TEXT, password TEXT)");

    }

    @Override
    public void onUpgrade(SQLiteDatabase MYDB, int oldVersion, int newVersion) {
        MYDB.execSQL("drop Table if exists users");
    }

    public Boolean insertData(String username, String firstname, String lastname, String password){
        SQLiteDatabase MYDB = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();
        contentValues.put("username", username);
        contentValues.put("firstname", firstname);
        contentValues.put("lastname", lastname);
        contentValues.put("password", password);
        long result = MYDB.insert("users",null, contentValues);
        if(result==-1) return false;
        else
            return true;
    }

    public Boolean checkusername(String username){
        SQLiteDatabase MYDB = this.getWritableDatabase();
        Cursor cursor = MYDB.rawQuery("Select * from users where username = ?", new String[] {username});
        if(cursor.getCount()>0)
            return  true;
        else
            return false;
    }

    public Boolean checkusernamepassword(String username, String password){
        SQLiteDatabase MYDB = this.getWritableDatabase();
        Cursor cursor = MYDB.rawQuery("Select * from users where username = ? and password = ?", new String[] {username, password});
        if(cursor.getCount()>0)
            return  true;
        else
            return false;
    }
}
