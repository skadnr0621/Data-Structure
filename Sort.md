## Sort 정렬

배열이나 리스트 정렬시 java.util.Arrays 클래스의 sort 메소드를 이용해서 정렬 로직 없이 정렬을 할 수 있습니다.

- **배열 오름차순 정렬**
  - Arrays.sort() 메서드의 매개값으로 기본 타입 배열이나 String 배열 지정시 자동으로 오름차순 정렬이 됩니다. **기본이 오름차순! /**
    ex) **Arrays.sort(arr);**
  
- **배열 내림차순\ 정렬**
  
  - 내림차순 정렬할 때는 Collections 클래스의 reverseOrder() 메서드를 사용합니다. 
    ex) Collections.reverseOrder()
    ex) **Arrays.sort(arr, Collections.reverseOrder());**
  - 기본타입 배열을 내림차순으로 정렬하고 싶을 시 기본 타입의 배열을 래퍼클래스로 만들어(?) Comparator를 두번째 인자로 넣어줘야 역순으로 정렬 가능. 
    - 주의! String은 기본타입이 아닙니다. 
    - 다른 for문도 연습하세요. 
  
- **배열 일부분 정렬**

  - 매개변수로 배열, 시작index, 끝index 를 넣어주면 해당 범위만 정렬할 수 있습니다. 
  - 끝 index는 항상 미만으로 적용됩니다. 
    ex) Arrays.sort(arr, 0, 4); // 0~3 요소만 정렬됩니다. 

- **객체 배열 정렬**

  - 객체로 이뤄진 배열의 경우는 객체 클래스가 Comparable 인터페이스의 CompareTo() 메서드를 구현하고 있어야 정렬이 됩니다. **나이별**로 정렬하는 예제를 보자면,

    ``` java
    import java.util.*;
    
    class People implements Comparable{
        private String name;
        private int age;
        
        public People(String name, int age){
            this.name = name;
            this.age = age;
        }
        
        public String print(){
            return name + "(" + age + ")";
        }
        
        @Override
        public int compareTo(People people){
            if(this.age < people.age){
                return -1;
            } else if(this.age == people.age){
                return 0;
            } else{
                return 1;  
            }
        }
    }
    
    public class Sort{
        public static void main(String[] args){
            People[] arr = {
                new People("상현", 20),
                new People("철수", 14),
                new People("경완", 31),
                new People("대호", 40),
                new People("지운", 34),
                           };
            Arrays.sort(arr); //오름차순 정렬
            
            for(People i : arr){ //오름차순 출력
                System.out.print("[" + i.print() + "]");
            }
            
            Arrays.sort(arr, Collections.reverseOrder());// 내림차순 정렬
            System.out.println();
            
            for(People i : arr){ // 내림차순 출력
                System.out.print("[" + i.print() + "]");
            }
        }
    }
    ```

    


### 예제로는 이해가 어려울 수 있다. 직접적으로 개념을 살펴보자. 

### Comparable과 Comparator의 이해

일단 Comparable과 Comparator 둘다 모두 **인터페이스**다. 즉 Comparable과 Comparator를 사용하고자 한다면 인터페이스 내에 선언된 메소드를 **"반드시 구현"**해야 한다. **인터페이스는 implements** 한다.
공식 문서를 살펴보면, 

- **Comparable** 인터페이스에는 **compareTo( T o)** 메소드 하나가 선언되어 있다. 이 말은 우리가 Comparable을 쓰고자 한다면 compareTo 메서드를 재정의(Override) 해야 한다는 것이다. 
- **Comparator**를 보면 선언된 메소드는 많지만, 우리가 실질적으로 구현해야 하는 것은 **compare(T o1, T o2)** 다.

일단 **인터페이스는 함수의 껍데기**만 있는 클래스라고 보면 된다. 인터페이스는 사물에 대해 기본적인 필수요소들만 선언해놓고, 이러한 필수요소들을 **구체적으로 구현하는 것을 클래스**라고 보면 됩니다. 이 **구체화**를 오버라이드(Override), 즉 **재정의**라고 부른다. 
그래서 인터페이스 파일의 경우 메소드를 선언만 해놓을 뿐 함수의 내용은 구체화하지 않는다. 이를 흔히 **추상 메소드** 라고 한다.



... 작성중



두 인터페이스의 차이점, 왜 객체 정렬을 할 때 둘 중 하나를 구현해야 하는지. 
프로젝트 등을 진행할 때는 객체를 중심으로 파일들을 나누고 기능들을 분리해서 따로 클래스를 만드는 등 별도의 클래스를 나누는 일이 허다하다. 
결과적으로 객체를 비교하고자 한다면 두 인터페이스에 대해서 필수적으로 알아야 한다. 



---

## 공부링크 : 

## https://coding-factory.tistory.com/549

## https://st-lab.tistory.com/243



