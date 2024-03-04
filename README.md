### [과제] 숙련주차 과제 답

#### - [o] 추가하기 버튼을 클릭해도 추가한 아이템이 화면에 표시되지 않음.
> >  액션을 호출하기 위한 useDispatch 선언이 안되어있어서 useDispatch 객체를 dispatch로 재선언한 후, dispatch 변수를 활용하 onSubmitHandler 함수에 추가했습니다.

    const dispatch = useDispatch();

    dispatch(addTodo({
      id,
      title: todo.title,
      body: todo.body,
      isDone: false,
    }))


---

#### - [o] 삭제 기능이 동작하지 않음.
> > modules > todos.js 에 모든 기능을 추가해둔 todos 라는 함수에 삭제에 대한 기능구현이 추가되어있지 않아서 
	삭제버튼 클릭한 아이디값만 빼고 나머지 투두리스트를 보여주도록 하는 DELETE_TODO case를 추가하였습니다. 
	
	case DELETE_TODO:
      		return {
        	todos: state.todos.filter((todo)=> todo.id !== action.payload)
      	};


---

#### - [o] 추가하기 버튼 클릭 후 기존에 존재하던 아이템들이 사라짐.
 > > 위의 코드 수정으로 인해 해당 오류는 안보이지만 
	버튼에도 따로 type을 정해주었습니다.

    	<StAddButton type="submit">추가하기</StAddButton>


---

####  - [o] 삭제 기능이 동작하지 않음.
> > modules > todos.js 에 모든 기능을 추가해둔 todos 라는 함수에 삭제에 대한 기능구현이 추가되어있지 않아서 
	삭제버튼 클릭한 아이디값만 빼고 나머지 투두리스트를 보여주도록 하는 DELETE_TODO case를 추가하였습니다. 

    case DELETE_TODO:
     return {
      todos: state.todos.filter((todo)=> todo.id !== action.payload)
    };

---

#### - [o] 상세 페이지에 진입 하였을 때 데이터가 업데이트 되지 않음.
> > useEffect 훅을 사용하여 컴포넌트가 마운트될때 getTodoByID 액션을 디스패치하여 id 에 해당하는 todo의 데이터를 가지고오도록 아래코드를 추가 수정하였습니다.

    useEffect(() => {
    dispatch(getTodoByID(id));
    }, [dispatch, id]);


---

#### - [o] 완료된 카드의 상세 페이지에 진입 하였을 때 올바른 데이터를 불러오지 못함.
> > 완료된 카드의 상세보기의 에서 link로 넘겨주는 값이 index로 로 들어가있어서 todo.id로 수정해주었습니다.

    <StLink to={`/${todo.id}`} key={todo.id}>
                  <div>상세보기</div>
                </StLink>

---

#### - [o] 취소 버튼 클릭시 기능이 작동하지 않음.
> > 완료 버튼클릭시  onClick={() => onToggleStatusTodo(todo.id)}
	현재 클릭한 값의 id 값을 받아와 작동이 잘되는 반면 현재 취소버튼에는 onClick={() => onToggleStatusTodo} id값을 불러와 전달해주지 않기 때문에 기능이 정상작동하지 않았습니다.때문에 아래 코드와 같이 코드를 수정해주었습니다.

    	 <StButton
                    borderColor="green"
                    onClick={()=>onToggleStatusTodo(todo.id)}
                  >
                    {todo.isDone ? "취소!" : "완료!"}
                  </StButton>


---

#### - [ ] 선택) 과제를 마쳤다면 배포도 한번 해볼까요?

> > 
    
