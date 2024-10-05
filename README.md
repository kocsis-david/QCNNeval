---

# Kvantum Konvolúciós Neurális Hálózat és Klasszikus Neurális Hálózat Összehasonlító Értékelés

## Projekt Áttekintés

Ez a projekt a kvantum konvolúciós neurális hálózat (QCNN) és egy klasszikus neurális hálózat (NN) teljesítményét hasonlítja össze a **CIFAR-10** képadatbázison, amely 10 különböző osztályú képet tartalmaz. A projekt célja annak vizsgálata, hogy a kvantuminformatikai módszerek hogyan teljesítenek azonos körülmények között egy hagyományos neurális hálózathoz képest.

## Adatkészlet

Az adatok a CIFAR-10 adatbázisból származnak, amely **50,000 tanítóképet** és **10,000 tesztképet** tartalmaz. A képeket 10 kategóriába sorolták, mint például repülőgép, autó, madár stb.

## Modell Felépítése

### Klasszikus Neurális Hálózat

A klasszikus modell egy egyszerű többrétegű perceptron, amely két sűrű réteget tartalmaz:

1. **Rejtett réteg**: 128 neuron, ReLU aktivációs függvény.
2. **Kimeneti réteg**: 1 neuron, sigmoid aktivációs függvény.

Az optimalizáláshoz Adam optimizálót használtunk, a célfüggvény pedig bináris keresztentrópia volt.

### Kvantum Konvolúciós Neurális Hálózat

A QCNN egy kvantum számítógépen futtatott hibrid modell, amely 10 kvantumbit (qubit) segítségével végzi az információ feldolgozását. A QCNN felépítése:

1. **Qubit állapotok**: Minden pixel adatot qubit forgatási szöggé alakítunk.
2. **Kvantum kapuk**: Minden qubit kap egy Rx és Ry forgatást, majd CNOT kapuk kapcsolják össze a qubitokat.

A kvantumrétegek között a differenciálás az Adjoint módszer segítségével történik, ami hatékonyabb és gyorsabb.

## Edzés és Értékelés

A projekt két különálló modellt alkalmazott az alábbi beállítások szerint:

- **QCNN**: 10 qubit, 3 rétegű kvantumkapu mélységgel, 50 epoch, 32-es batch méret.
- **Klasszikus NN**: 128 neuronos rejtett réteg, 50 epoch, 32-es batch méret.

### Eredmények

Az alábbi diagramok mutatják a két modell tanulási görbéit:

- **Veszteség (loss)**: Mind a kvantum, mind a klasszikus modell tanulási veszteségét ábrázolja az edzési és validációs adatokon.
- **Pontosság (accuracy)**: A QCNN és a klasszikus NN teljesítménye az edzési és validációs adatokon.

### Ábrák

#### Veszteség Diagram

![Loss Diagram](cifar10_classical_vs_quantum_loss.png)

#### Pontosság Diagram

![Accuracy Diagram](cifar10_classical_vs_quantum_accuracy.png)

### Végső Teszt Pontosság

A teszt során a QCNN **0.68** pontosságot ért el, míg a klasszikus modell **0.67** pontosságot mutatott. Ez jelzi, hogy a kvantum számítási modell is képes a klasszikus módszerekkel versenyezni bizonyos problémákon.

## Telepítés és Futtatás

1. Telepítse a következő függőségeket:
   ```bash
   pip install tensorflow tensorflow-quantum cirq sympy
   ```
2. Töltse le a CIFAR-10 adatbázist.
3. Futtassa a `qcnn_vs_nn.py` fájlt:
   ```bash
   python qcnn_vs_nn.py
   ```

## Következtetés

A QCNN ígéretes eredményeket mutatott a klasszikus módszerekkel szemben, különösen a kis adathalmazokon való edzés során. Ez a projekt kiemeli a kvantumszámítási technikák hatékonyságát bizonyos feladatokban, de további fejlesztések szükségesek a nagyobb adatbázisok és mélyebb modellek esetében.

---

Ez a README dokumentum áttekintést nyújt a projekt struktúrájáról és a két hálózat teljesítményének összehasonlításáról.
