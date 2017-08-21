# ChatFilter

---

This is a public list for badwords used by my ChatFilter Plugin!
You wanna try my plugin? Contact me via mail

---

You wanna use this list yourself?

Here a method how you can get get a List of these bad words:


```java

import java.io.File;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.net.URL;
import java.nio.channels.Channels;
import java.nio.channels.ReadableByteChannel;
import java.util.ArrayList;
import java.util.List;
import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;

	public List<String> getBadWords(File datafolder) {
		List<String> list = new ArrayList<>();
		try {
			File gfile = new File(datafolder.getPath() + "/globalwords.json");
			URL url = new URL("https://raw.githubusercontent.com/zM4xi/ChatFilter/master/words.json");
			ReadableByteChannel rbc = Channels.newChannel(url.openStream());
			FileOutputStream fos = new FileOutputStream(datafolder.getPath() + "/globalwords.json");
			fos.getChannel().transferFrom(rbc, 0, Long.MAX_VALUE);
			JSONParser parser = new JSONParser();
			Object obj = parser.parse(new FileReader(gfile));
			JSONObject jsonObject = (JSONObject) obj;
			JSONArray array = (JSONArray) jsonObject.get("words");
			for (int i = 0; i < array.size(); i++) {
				list.add(array.get(i).toString());
			}
		} catch (ParseException | IOException e) {
			e.printStackTrace();
		}
		return list;
	}
  ```
  ---
