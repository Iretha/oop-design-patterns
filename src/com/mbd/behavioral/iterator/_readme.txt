Използва се за обхождане и за достъп до елементи на агрегатни структури от данни, без да 
дава представа за вътрешната им имплементация. Този шаблон позвалява висока абстракция на
обектите, като при необходимост от промяна в имплементацията, това да не налага допълнителен 
рефактор извън нея.

Разгледаният пример показва точно това:
Имаме два интерфейса, един който представлява колекцията и един, който представлява итератор 
върху дадената колекция. Имплементацията на двата интерфейса остава напълно скрита в класа
AlbumCollection. При необходимост от каквато и да е промяна в имплементацията, промяната ще
остане напълно скрита за външните класове, като достъпът до елементите ще се запази непроменен,
каквато е и целта при използването на този патърн.

Ето и примерен код, който показва как се използва:
		
		ICollection<Album> myCollection = new AlbumCollection();
		IIterator<Album> it = myCollection.iterator();

		Album curr = null;
		while (it.hasNext()) {
			curr = it.next();
			System.out.println(curr.toString());
		}
		
		