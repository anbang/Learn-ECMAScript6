#�鼶������

## 1��ES6�������ϸ�ģʽ�²ſ�������ʹ�ã�
#### �ϸ�ģʽ����ͨģʽ������
    - 1���ϸ�ģʽ�ὫJavaScript����ֱ�ӱ�����ԵĴ���
    - 2���ϸ�ģʽ������һЩ���������Ż��Ĵ���,ͬ���Ĵ�����Щʱ���ϸ�ģʽ��ȷ��ϸ�ģʽ�¸��졣
    - 3���ϸ�ģʽ������һЩ�п�����δ���汾�ж�����﷨��
    
#### ��Ϊ����ʹ��ES6ʱ�򣬱������ϸ�ģʽ�²ſ�������ʹ�ã����ᱨ����
    - �ϸ�ģʽ����Ӧ�õ�����script��ǩ��ĳ�������С�
    
    - 1��Ϊ����script��ǩ�����ϸ�ģʽ�� ��Ҫ���������֮ǰ��һ���ض���� "use strict"; ���� 'use strict';��
    // ������䶼�����ϸ�ģʽ���﷨
    "use strict";
    let v = "Hi!  I'm a strict mode script!";
    
    - 2��Ҫ��ĳ�����������ϸ�ģʽ���ð� "use strict"; (�� 'use strict'; )�������ں������������֮ǰ��
    // ���������ϸ�ģʽ�﷨
    function strict(){
      'use strict';
      return "Hi!  I'm a strict mode function!" ;
    }
    
    function notStrict() { 
      return "I'm not strict.";
    }
    
## 2��let��ʹ�ã�var�������棩
    ES6��������һ��let��������{}�� if�� for���������÷�ͬvar�����������޶��ڿ鼶��let�����ı��������ڱ���������var�б���������Ч������
    let �����ѱ����������������ڿ鼶���С��� var��ͬ���ǣ�var ��������Ҫô��ȫ�ֵģ�Ҫô�Ǻ������ģ����޷��ǿ鼶�ġ�
    
##### let vs var     ��let���������ǿ飬��var���������Ǻ�����
    'use strict';
    var a = 5;
    var b = 10;
    if (a === 5) {
      let a = 4; // �����������if���������
      var b = 1; // �������������ջ�ڴ���ģ�
      console.log(a);  // 4
      console.log(b);  // 1
    } 
    console.log(a); // 5
    console.log(b); // 1
    
##### let��ѭ���� ������ʹ��let�ؼ��ְ󶨱�����ѭ���ķ�Χ��������ʹ��һ��ȫ�ֱ���(ʹ��var)���塣��

    'use strict';
    for (let i = 0; i < 10; i++) {
      console.log(i); // 0, 1, 2, 3, 4 ... 9
    }
    console.log(i); // i is not defined
    ���汨������Ϊ����i��������for�������������С�let�����鼶����������ģ�ʹ��var����һ��ȫ�ֱ�����
## 3��const���÷������������Ա����¸�ֵ,���Ҳ��ܱ��ظ�����.��

    const�����������һ������,����ȫ�ֻ�ֲ��ĺ���������
    
    һ������������ȫ�ֵĻ����Ǿֲ���,������ѭ�������ͬ�����������
    
    һ�����������Ա����¸�ֵ,���Ҳ��ܱ��ظ�����.����,��Ȼ����������һ��������ʱ�򲻽��г�ʼ��,����������û�������,��Ϊ���������ֵ��Զ�ᱣ��undefined��
    
    һ���������ܺ��������������ڵ�������������ӵ����ͬ�����ơ�
    
    �����������ʾ�˳�������Ϊ��
    const num = 10;
    num =20;
    console.log(num); // 10
    
    ���������������������num��������var num����ʱ�ᱨ����num�Ѿ�������
    const num = 10;
    var num = 20;
    console.log(num); // 'num' has already been declared
    
## 4���鼶������  ��let�������԰������������ڿ鼶��ͬʱconst���Ա�֤���������ظ���ֵ��������
    �ܶ������ж��п鼶������JavaScriptʹ��var������������function�����������򣬴����š�{}�� ȴ�޶�����var����������var�����ı������б���������declaration hoisting����Ч����
    
    ES6��������һ��let��������{}�� if�� for���������÷�ͬvar�����������޶��ڿ鼶��let�����ı��������ڱ���������
    'use strict';
    function f1() {
      var a = 1;
      let n = 2;
      if (true) {
          var a = 20;
          let n = 10;
      }
      console.log(n); // 2
      console.log(a); // 20
    }
    f1();