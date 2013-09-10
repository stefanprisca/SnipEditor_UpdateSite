SnipMatch_UpdateSite
=====================
In order to install and use this, follow the steps: <br>
  (1)clone the repo to the local pc<br>
  (2)open eclipse IDE<br>
  (3)go to Help->Install New Software<br>
  (4)Select Add Site->Local<br>
  (5)chose the downloaded folder "repository"<br>
  (6)click install<br>
  <br>
In order to create code snippets:<br>
<br>
  (1)Create a new Java Project<br>
  (2)Add new file<br>
  (3)Set the file name file_name.cSnip (must have .cSnip extension)<br>
  (4)Confirm XText usage.<br>
<br>

Some using instructions:<br>
<p>
  (1) imports have the following format:<br>
    <br>
    ~ ${import(library.you.want.to.import.*)}<br>
    ~ ${import(library.you.want.to.import.specificClass)}<br>
    <br>
</p>
<p>
  (2) variables and attributes can be declared like in java(with a simple name) or using one 
      of the following expressions:<br>
     <br>
      ~ varName <br>
      ~ ${varName} <br>
      ~ ${freeName(varName)} <br>
      ~ ${newName(varName)} <br>
    <br>
    Each of the last three will be translated to ${varName}, so the variable / attribute will be accessed<br> 
    through this id (new ids can be introduced at any time if needed) <br>
</p>
<p>
  (3) only java types are supported! in order to use a type, you must explicitly import it(except for basic String, Integer, etc.).<br>
  Some quick fixes will be available to ease codding.<br>
  Types can be accessed in the following manner:<br>
      <br>
      ~ type_name <br>
      ~ ${elemType(type_name)} <br>
    <br>
  Both access the same type ( type_name ). Maybe somewhere in the future, abstract types that will<br> 
    be deduced from context will be availabe.(e.g.: ${some_Array_type})<br>
</p>
<p>
(4) the rest of the expressions are similar to java, except for the for loop expression which supports only <br>
  the iterator syntax, the other one will come in a future update.<br>
</p>  
<br>
An example:
<pre>
${import(org.eclipse.xtext.xbase.lib.*)}
${import(java.util.Locale.Builder)}

class c1{
  public void m1(){
  	String[] a=new String [2];
		${elemType(Builder)} ${freeName(b)}=new Builder();
		${b}.addUnicodeLocaleAttribute("MyBuilder");
		System.out.print(a);
		if(a instanceof String[]){
			super.toString();
		}
		for(${s} : a){
			System.out.println(${s});
			${cursor}
		}
		while('${dollar}' == '$' ){
			System.out.println(a);
		}
	} 
}  
</pre>
