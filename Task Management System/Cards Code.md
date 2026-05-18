### Card.jsx
```JSX
import { BsListTask } from 'react-icons/bs'
import { FaRegClock, FaRegCheckCircle } from 'react-icons/fa'
import { MdOutlineCheckBoxOutlineBlank } from 'react-icons/md'

export function StatCards() {
    return (
        <div id="cards-container">
            <div className="card">
                <div className="card-header">
                    <span>Total Tasks</span>
                    <div className="icon-circle blue">
                        <BsListTask />
                    </div>
                </div>
                <h2>3</h2>
            </div>

            <div className="card">
                <div className="card-header">
                    <span>In Progress</span>
                    <div className="icon-circle yellow">
                        <FaRegClock />
                    </div>
                </div>
                <h2>1</h2>
            </div>

            <div className="card">
                <div className="card-header">
                    <span>Completed</span>
                    <div className="icon-circle green">
                        <FaRegCheckCircle />
                    </div>
                </div>
                <h2>1</h2>
                <p>33% completion rate</p>
            </div>

            <div className="card">
                <div className="card-header">
                    <span>To Do</span>
                    <div className="icon-circle grey">
                        <MdOutlineCheckBoxOutlineBlank />
                    </div>
                </div>
                <h2>1</h2>
            </div>
        </div>
    )
}
```

### Card.css:

```JSX
#cards-container {
    display: flex;
    gap: 16px;
    padding: 16px;
}

.card {
    background: white;
    border-radius: 12px;
    padding: 16px;
    flex: 1;
    box-shadow: 0 1px 4px rgba(0,0,0,0.1);
}

.card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 16px;
}

.icon-circle {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
}

.blue   { background-color: #e0eaff; color: #3b82f6; }
.yellow { background-color: #fef3c7; color: #f59e0b; }
.green  { background-color: #d1fae5; color: #10b981; }
.grey   { background-color: #f3f4f6; color: #6b7280; }
```