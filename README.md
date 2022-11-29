# Oyun
---
Bir köprü oluşturun, karşı platforma geçin ve yıldıza ulaşın.

![](https://github.com/edadural/Game/blob/main/img/bb5.png)

### Nasıl Oynanır? 
- Space tuşu ile köprünün boyutunu karşı platformdaki renki kısıma gelecek şekilde arttırın.
- Platforma geçmek için yön tuşunu kullanın. 
- Köprü boyutunun platformun dışına çıkmadığına dikkat edin.
- ESC tuşu ile menü ekranını açabilirsiniz. Oyunu durdurabilir, kaldığınız yerden devam ettirebilir veya tekrar başlatabilirsiniz.

##### Tuşlar:
- Space : Köprünün boyunu ayarlamak için
- Sağ yön tuşu (→) : Karakteri hareket ettirmek için 
- ESC : Menu ekranı

![](https://github.com/edadural/Game/blob/main/img/bb3.png)

---

Köprünün boyutunu ayarlamak ve hareket etmesini sağlamak için yazdığımız kod
```
    if(Input.GetAxisRaw("Jump") == 1f && turnCount == 1){
        transform.localScale += new Vector3(0f,0.2f,0f);
    } 
    else if(Input.GetAxisRaw("Jump") == -1f){
        turn = true;
        if(turn == true && turnCount == 1){
            transform.rotation = transform.rotation * Quaternion.Euler(0,0,-90);
            turn = false;
            turnCount -= 1;             
        }
    }
```
Oyuncunun hareket etmesi için yazdığımız kod
```
    if(turnCount == 0){
        playerControl.transform.Translate(Vector3.right * Time.deltaTime * playerScript.speed);      
    }
```
Oyuncunun yıldıza ulaştığında yıldızın yok olması için yazdığımız kod
```
    private void OnTriggerEnter(Collider other){
        Destroy(this.gameObject);  
    }
```

Oyuncunun yıldıza ulaştığında oyuncunun durması için yazdığımız kod
```
    private void OnTriggerEnter(Collider other){
        if(other.tag == "Target"){
            speed = 0f;
        }   
    }
```
Oyunu durdurmak ve devam ettirmek için yazdığımız kod
```
    public void ResumeGame(){
        if (pause){
            Time.timeScale = 1;
            pause = false;
        } else {
            Time.timeScale = 0;
            pause = true;
        }
        ana_kanvas.enabled = false;
    }
```
Oyunu tekrardan başlatmak için yazdığımız kod
```
    public void RestartGame(){
        SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        ResumeGame();
    }
```

---
### Hazırlayanlar
- Rumeysa Emine Şahin
- Eda Dural


