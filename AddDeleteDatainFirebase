import { initializeApp } from "firebase/app";
import { collection, doc, deleteDoc, getDocs, getFirestore , addDoc} from "firebase/firestore";
// import addDoc function ffrom firestore
import { getAuth } from "firebase/auth";
const firebaseConfig = {
  apiKey: "AIzaSyD6FF-MuUqEi-5QuI7pvig-mRT71K-56MU",
  authDomain: "netflex-clone-25f1f.firebaseapp.com",
  projectId: "netflex-clone-25f1f",
  storageBucket: "netflex-clone-25f1f.appspot.com",
  messagingSenderId: "813413117409",
  appId: "1:813413117409:web:d76e5f7172eb6637d2f6a0",
  measurementId: "G-X1V8PVD2HF"
};

initializeApp(firebaseConfig);
export const auth = getAuth()

const db = getFirestore();

const collectionReference = collection(db, 'books')
getDocs(collectionReference)
.then((snapshot) =>{
  let books = []
  snapshot.docs.forEach((doc) => {
    books.push({...doc.data(), id: doc.id})
console.log(books)  })

}).catch((err) => {
  console.log(err.message)
})

export default auth;

const addBookForm = document.querySelector('.add')
addBookForm.addEventListener('submit', (e) => {
 e.preventDefault()
//  import addDoc() dunction it takes 2 argument 1st agrument is collection reference so the firestore knows what collection that we want to add a new document bcz we might have multiple differt collection
// 2nd argument is an object and this object represents the new documnet that we want to add to to that particular collection teh documnet has different fields we need to use properties and values for those fields 
// so our documnets need a title property and an author property we need to grab those property values from our form in html input we have name of title and author
// we need to grab form reference which is stored in constant addBookForm, deleteBookForm  addBookForm => we grab that the can use dot noation to grab a specific input field inside that form by using the name attribue
// so now we have these two object with these two properties title and author and we are calling this function add doc we saying look into the book collection and add this as a new document inside there and do it for us now it is asynchronous and it will return a promise so if we want to take on then mmehtod which is going to fire a function once this is complete and we can do something inside that function
// i would reset the form so that it empties the input fields for us and we can easily type in a new one  to do that we can use reset method
// on form rederence so grab that paste it in and then  we can use a method on that called reset like and invoke that
addDoc(collectionReference, { 
  title: addBookForm.title.value,
  author: addBookForm.author.value, 
 }).then(() => {
  addBookForm.reset()
 })
})


// for deleting document we need 2 fun deleteDoc() and doc . Doc function is similar to collection function in that it gets us a reference but this time instead of getting us a reference to a collection it gets us a reference to a doc bcz in order to delete a document we need a reference to that document to day look this iis the one we want to delete
// inside this function  i want to get a reference to the documents that i want to delete so i will create a consttant
// const docRef = doc() 
// this take 3 argument 1st db 2nd collection name 3rd id of the document that we want to reference to inside that collection
// remember we ask user to input the id into field so all we need to grab the value of that input field and we can we grab the values of these inputs 3rd : deleteBookForm which is the reference of our form and then the name of that input field which is id in this case dBf.id.value and that gets us the id that a user has entered in to that input field so now we are storing that inside doc red and now we want
// now to delete that document we will call deleteDoc() function and we need to padd docRef 
const deleteBookForm = document.querySelector('.delete')
deleteBookForm.addEventListener('submit', (e) => {
  e.preventDefault()
  const docRef = doc(db, 'books', deleteBookForm.id.value) //invoke doc function inside docRef this is how we get document reference
  deleteDoc(docRef) //that goes out and delete that document and this is asynchronous so i can tackle a then method if i want to fire a function when it is completed when it is deled it and i want to do reset the deleteBookForm
.then(() => {
  deleteBookForm.reset()
})
})

