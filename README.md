LAB 19 - Room MVVM Repository ViewModel LiveData RecyclerView
Application Android Java de notes locales persistantes avec Room et une architecture MVVM complete.

Fonctionnalites
Champ titre.
Champ description.
Bouton d'ajout.
Liste des notes avec RecyclerView.
Suppression par clic long.
Persistance locale via Room.
Architecture
Entity : Note, structure des donnees persistees.
DAO : NoteDao, interface d'acces aux donnees.
RoomDatabase : NoteDatabase, point central de SQLite.
Repository : NoteRepository, couche intermediaire entre Room et ViewModel.
ViewModel : NoteViewModel, logique de presentation et conservation d'etat.
LiveData : observation automatique respectant le cycle de vie de l'Activity.
RecyclerView : affichage performant de la collection de notes.
Thread principal
Room ne doit pas executer les operations potentiellement bloquantes sur le thread UI. Dans ce projet, insert et delete passent par un ExecutorService dans le Repository. La lecture retourne un LiveData<List<Note>>, observe par l'Activity.

Limite ViewModel
Le ViewModel survit a une rotation, un changement de configuration et une recreation d'Activity. Il ne remplace pas a lui seul la gestion du process death. Pour cela, Android propose notamment Saved State for ViewModel.

Versions AndroidX
Versions stables utilisees :

implementation 'androidx.room:room-runtime:2.8.4'
annotationProcessor 'androidx.room:room-compiler:2.8.4'
implementation 'androidx.lifecycle:lifecycle-viewmodel:2.10.0'
implementation 'androidx.lifecycle:lifecycle-livedata:2.10.0'
implementation 'androidx.recyclerview:recyclerview:1.4.0'
Lancer
Ouvrir ce dossier dans Android Studio, puis lancer l'application.

Depuis PowerShell :

.\gradlew.bat assembleDebug
