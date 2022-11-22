package jdbcMongo;

import com.mongodb.*;
 
public class UpdateJDBC {

	public static void main(String[] args) {
		// create db
		
		MongoClient mongo = new MongoClient("localhost",27017);
		
		DB db = mongo.getDB("mydb");
		
		DBCollection col = db.getCollection("students");
		
		//Before update
		DBCursor cursor = col.find();
		while(cursor.hasNext())
			System.out.println(cursor.next());
	

	
	
		
		BasicDBObject oldDoc = new BasicDBObject("name","atharv");
		BasicDBObject newDoc = new BasicDBObject("name","atharva");
		BasicDBObject updateDoc = new BasicDBObject("$set",newDoc);
		
		col.update(oldDoc,updateDoc);
		
		
		//After update
		DBCursor cursor1 = col.find();
		while(cursor1.hasNext())
			System.out.println(cursor1.next());
	}

}
