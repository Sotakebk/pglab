# Dodatek: Wersjonowanie projektu

Temat: Wersjonowanie projektu

Cel: Poznanie systemu Unity Version Control

Tabela zawartości
---
- [Dodatek: Wersjonowanie projektu](#dodatek-wersjonowanie-projektu)
  - [Tabela zawartości](#tabela-zawartości)
  - [Unity Version Control](#unity-version-control)
    - [Włączenie](#włączenie)
    - [Używanie](#używanie)
      - [Dodawanie użytkowników](#dodawanie-użytkowników)
      - [Wprowadzanie zmian](#wprowadzanie-zmian)
    - [Unity DevOps Version Control](#unity-devops-version-control)
    - [Znane problemy](#znane-problemy)

## Unity Version Control

Unity Version Control (wcześniej znany jako Plastic SCM) to system kontroli wersji zaprojektowany specjalnie z myślą o potrzebach zespołów tworzących gry i inne projekty w Unity. Jest alternatywą dla Git, który gorzej radzi sobie z plikami binarnymi oraz dużymi plikami, o ile nie używa się Git LFS.

Używanie Unity Version Control jest bardzo podobne do Git, z podobnymi nazwami na analogiczne elementy: `changeset` zamiast `commit`, `branch`, `merge`, itd.

Należy mieć na uwadze, że on-prem, tzn. własne hostowanie serwera hostującego kod źródłowy, wymaga zakupu odpowiedniej wersji na specjalnej licencji. Kolejnym ograniczeniem jest limit przestrzeni dyskowej przeznaczonej na pliki projektu, który wynosi 10 GB dla całej 'organizacji'.

Interfejs edytora jest dość nieprzystępny na moment pisania tego konspektu. [Dedykowany klient](https://docs.unity.com/ugs/en-us/manual/devops/manual/version-control-desktop-client) jest znacznie wygodniejszy, przystępniejszy, oraz pozwala na wykonywanie wielu operacji które są niedostępne, lub trudne do odnalezienia w interfejsie edytora.

### Włączenie

Włączenie UVC wymaga integracji z usługami chmurowymi. Nowo tworzony projekt można odpowiednio ustawić tak, aby został automatycznie powiązany z odpowiednim zasobem chmurowym, lub istniejący już projekt może zostać zarejestrowany.

![konfiguracja przy tworzeniu projektu](./media/creating-new-project.png)

Aby zarejestrować istniejący projekt, należy otworzyć odpowiednie okno poprzez rozwijane menu (`Window->Unity Version Control`).

![dodawanie projektu 1](./media/uvc-complete-setup.png)
![dodawanie projektu 2](./media/uvc-complete-setup2.png)

Na stronie [https://cloud.unity.com/home/](https://cloud.unity.com/home/) powinna pojawić się zakładka z nowo dodanym projektem.

![alt text](./media/cloud-unity-com-project.png)

### Używanie

#### Dodawanie użytkowników

Aby móc pracować nad jednym projektem z wieloma osobami, należy dodać je do organizacji, lub zaprosić do projektu.

![zaproszenie do projektu](./media/add-contributors.png)
![zaproszenie do projektu](./media/invite-project-members.png)

![członkowie organizacji](./media/organization-members.png)
![członkowie organizacji](./media/invite-organization-members.png)

Dodany użytkownik powinien móc dodać projekt z repozytorium poprzez program Unity Hub:

![dodaj z repozytorium](./media/add-from-repository.png)
![lista projektów](./media/add-from-repository2.png)

#### Wprowadzanie zmian

Po wprowadzeniu jakichkolwiek zmian w projekcie, lista oczekujących zmian (`Pending Changes`) będzie zawierać informacje o tym jaki plik został dodany, usunięty, lub zmodyfikowany. Można również podejrzeć zmiany w plikach testowych, i porównać z poprzednią wersją.

![changes](./media/changes.png)

`Changesets` zawiera historię zmian.

![changesets](./media/changesets.png)

W typowej pracy, każda osoba ma własną gałąź, na której pracuje nad osobnym, możliwie niezależnym elementem. W innym wypadku zmiany wprowadzane na jednej gałęzi mogą potencjalnie powodować problemy z ciągłymi konfliktami, złe zmiany są problematyczne w cofaniu, itp. tak, jak używając git.

Gałęzie można utworzyć w sposób zaprezentowany poniżej.

![branches](./media/branches.png)

Lokalny projekt można przełączać między gałęziami za pomocą opcji `Switch workspace to this branch`.

Po wykonaniu swoich zmian, gałąź można scalić `merge` do 'głównej' gałęzi. W tym celu należy przełączyć się na gałąź docelową, i wybrać `merge from this branch...` na drugiej gałęzi.

![merge from this branch](./media/merge-from-this-branch.png)

W przypadku konfliktów, czyli różnych zmian w tych samych plikach, scalanie wymaga ręcznego zmodyfikowania kodu i zaakceptowania wynikających zmina.

![konflikty](./media/conflicts.png)

### Unity DevOps Version Control

Unity ma również [dedykowane narzędzie dla obsługi systemu wersjonowania](https://docs.unity.com/ugs/en-us/manual/devops/manual/version-control-desktop-client) analogiczne do np. SourceTree dla `git`. Ma ono znacznie bardziej przystępny interfejs użytkownika, oraz pozwala na lepszą wizualizacje zmian, oraz natywne rozwiązywanie konfliktów.

![alt text](./media/udvvc-branches.png)

![alt text](./media/udvvc-merge.png)

Interfejs pozwala również na wiele więcej operacji, wiele z nich nie jest dostępne w interfejsie edytora. Wszystko, co można zrobić w edytorze, działa analogicznie w tym interfejsie.

![alt text](./media/udvvc-options.png)


### Znane problemy

W razie wystąpienia poniższego błędu, zwykłe zamknięcie i ponowne otwarcie projektu może pomóc. W innym przypadku, informacje dostępne w internecie mogą pomóc.

![nietypowy błąd](./media/error.png)
